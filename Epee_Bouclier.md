# UE 5.6 Blueprint — Attaquer avec une épée et bloquer avec un bouclier

> Objectif : créer un système simple en Blueprint où le joueur peut attaquer avec une épée, bloquer avec un bouclier, réduire ou annuler les dégâts reçus de face, et empêcher l’attaque pendant le blocage.

## 1. Préparation du projet

### Assets nécessaires

- Un `Character Blueprint`, par exemple `BP_PlayerCharacter`
- Une épée, par exemple `SM_Sword` ou `SK_Sword`
- Un bouclier, par exemple `SM_Shield` ou `SK_Shield`
- Une animation d’attaque, par exemple `AM_Attack_01`
- Une animation de blocage ou une pose de blocage, par exemple `AM_Block_Start` / `AM_Block_Idle`
- Un ennemi ou une cible avec une fonction de dégâts

## 2. Inputs avec Enhanced Input

Dans UE 5.6, utilise le système **Enhanced Input**.

Crée ces assets :

```text
IA_Attack       Input Action / Boolean
IA_Block        Input Action / Boolean
IMC_Combat      Input Mapping Context
```

Dans `IMC_Combat`, ajoute :

```text
IA_Attack  -> Left Mouse Button / Gamepad Right Trigger
IA_Block   -> Right Mouse Button / Gamepad Left Trigger
```

Dans `BP_PlayerCharacter`, au `BeginPlay` :

```text
Event BeginPlay
→ Get Player Controller
→ Get Local Player Subsystem Enhanced Input
→ Add Mapping Context
   Mapping Context = IMC_Combat
   Priority = 0
```

## 3. Composants du personnage

Dans `BP_PlayerCharacter`, ajoute ou vérifie :

```text
Mesh
SwordMesh
ShieldMesh
SwordCollision
ShieldCollision
```

Hiérarchie conseillée :

```text
BP_PlayerCharacter
├── CapsuleComponent
├── Mesh
│   ├── SwordMesh
│   │   └── SwordCollision
│   └── ShieldMesh
│       └── ShieldCollision
```

Attache l’épée et le bouclier à des sockets du squelette :

```text
SwordMesh  -> hand_r_socket
ShieldMesh -> hand_l_socket
```

Crée ces sockets dans le Skeleton si nécessaire.

## 4. Variables Blueprint

Dans `BP_PlayerCharacter`, crée :

```text
IsAttacking       Boolean = false
IsBlocking        Boolean = false
CanAttack         Boolean = true
AttackDamage      Float = 25.0
BlockDamageRatio  Float = 0.25
BlockAngle        Float = 90.0
HitActors         Array Actor
```

Explication :

```text
IsAttacking       Le joueur est en train d’attaquer
IsBlocking        Le joueur tient le bouclier levé
CanAttack         Empêche le spam d’attaque
AttackDamage      Dégâts de l’épée
BlockDamageRatio  0.25 = le joueur reçoit 25 % des dégâts pendant un blocage réussi
BlockAngle        Angle frontal dans lequel le blocage fonctionne
HitActors         Évite de toucher plusieurs fois la même cible pendant un swing
```

## 5. Collision de l’épée

Sélectionne `SwordCollision` :

```text
Collision Enabled: No Collision par défaut
Generate Overlap Events: true
Collision Preset: Custom
Object Type: WorldDynamic
Pawn: Overlap
WorldDynamic: Overlap
WorldStatic: Ignore
```

Au début du jeu :

```text
SwordCollision → Set Collision Enabled = No Collision
```

L’épée ne doit être active que pendant la fenêtre de frappe.

## 6. Fonction Attack

Crée une fonction ou un Custom Event :

```text
Custom Event Attack
```

Logique :

```text
Attack
→ Branch CanAttack == true
→ Branch IsBlocking == false
→ Set CanAttack = false
→ Set IsAttacking = true
→ Clear HitActors
→ Play Anim Montage AM_Attack_01
→ Delay 0.2
→ SwordCollision Set Collision Enabled = Query Only
→ Delay 0.25
→ SwordCollision Set Collision Enabled = No Collision
→ Set IsAttacking = false
→ Delay 0.3
→ Set CanAttack = true
```

Le premier `Delay` représente le moment où l’épée commence réellement à frapper. Ajuste les valeurs selon ton animation.

## 7. Input attaque

Dans l’Event Graph :

```text
IA_Attack Started
→ Attack
```

Optionnel : bloque le mouvement pendant l’attaque courte :

```text
Character Movement → Disable Movement
Delay 0.45
Character Movement → Set Movement Mode Walking
```

## 8. Détection de touche avec l’épée

Sur `SwordCollision` :

```text
On Component Begin Overlap SwordCollision
→ Other Actor
→ Branch Other Actor != Self
→ Contains HitActors Other Actor ?
```

Si `false` :

```text
Add Other Actor to HitActors
→ Apply Damage
   Damaged Actor = Other Actor
   Base Damage = AttackDamage
   Event Instigator = Get Controller
   Damage Causer = Self
```

Blueprint simplifié :

```text
OnComponentBeginOverlap SwordCollision
→ Branch IsAttacking
→ Branch OtherActor != Self
→ Branch NOT HitActors Contains OtherActor
→ Add OtherActor to HitActors
→ Apply Damage OtherActor AttackDamage
```

## 9. Blocage avec le bouclier

Crée deux Custom Events :

```text
StartBlock
StopBlock
```

### StartBlock

```text
StartBlock
→ Branch IsAttacking == false
→ Set IsBlocking = true
→ Set CanAttack = false
→ Play Anim Montage AM_Block_Start
→ Character Movement Max Walk Speed = 200
```

### StopBlock

```text
StopBlock
→ Set IsBlocking = false
→ Set CanAttack = true
→ Stop Anim Montage AM_Block_Start ou passer vers Block_End
→ Character Movement Max Walk Speed = 500
```

## 10. Input blocage

Dans l’Event Graph :

```text
IA_Block Started
→ StartBlock

IA_Block Completed
→ StopBlock

IA_Block Canceled
→ StopBlock
```

## 11. Réduction des dégâts pendant le blocage

Dans `BP_PlayerCharacter`, utilise l’événement :

```text
Event AnyDamage
```

Logique :

```text
Event AnyDamage
→ Branch IsBlocking
```

Si le joueur ne bloque pas :

```text
Health = Health - Damage
```

Si le joueur bloque, vérifie que l’attaque vient de devant.

Crée une fonction :

```text
IsDamageFromFront
```

Entrées :

```text
DamageCauser Actor
```

Sortie :

```text
Return Boolean
```

Logique :

```text
Self Forward Vector = Get Actor Forward Vector
Direction To Attacker = DamageCauser Location - Self Location
Normalize Direction To Attacker
Dot Product = Dot(Self Forward Vector, Direction To Attacker)
```

Condition :

```text
Dot Product > 0.3
```

Interprétation simple :

```text
Dot > 0.3   L’attaquant est devant le joueur
Dot < 0     L’attaquant est derrière le joueur
```

Dans `Event AnyDamage` :

```text
Event AnyDamage
→ Branch IsBlocking
   false:
      Health = Health - Damage
   true:
      Branch IsDamageFromFront(DamageCauser)
         true:
            FinalDamage = Damage * BlockDamageRatio
            Health = Health - FinalDamage
            Play Block Impact Sound / Animation
         false:
            Health = Health - Damage
```

Pour un blocage parfait :

```text
BlockDamageRatio = 0.0
```

Pour un blocage partiel :

```text
BlockDamageRatio = 0.25 ou 0.5
```

## 12. Animation Blueprint

Dans l’Animation Blueprint du personnage :

Crée ces variables :

```text
IsBlocking
IsAttacking
Speed
```

Depuis `BP_PlayerCharacter`, mets à jour `IsBlocking` dans l’AnimBP, ou récupère la variable via :

```text
Try Get Pawn Owner
→ Cast to BP_PlayerCharacter
→ Get IsBlocking
```

Dans l’AnimGraph, ajoute un slot de montage :

```text
Locomotion State Machine
→ Slot DefaultSlot
→ Output Pose
```

Les Animation Montages ont besoin d’un slot pour s’afficher correctement dans l’AnimGraph.

## 13. Amélioration : collision de bouclier physique

Le blocage peut être uniquement logique avec `IsBlocking`, mais tu peux aussi activer une collision de bouclier.

Sur `ShieldCollision` :

```text
Collision Enabled: Query Only
Generate Overlap Events: true
Collision Preset: Custom
Pawn: Ignore
WorldDynamic: Overlap
```

Pendant le blocage :

```text
StartBlock
→ ShieldCollision Set Collision Enabled = Query Only

StopBlock
→ ShieldCollision Set Collision Enabled = No Collision
```

Tu peux utiliser cette collision pour déclencher :

```text
Son d’impact
Effet visuel
Stagger de l’ennemi
Parade parfaite
```

## 14. Système de parade optionnel

Ajoute une variable :

```text
IsPerfectParryWindow Boolean = false
```

Dans `StartBlock` :

```text
Set IsPerfectParryWindow = true
Delay 0.2
Set IsPerfectParryWindow = false
```

Dans `Event AnyDamage` :

```text
If IsBlocking == true
→ If IsPerfectParryWindow == true
   → Damage = 0
   → Stun Attacker
   → Play Parry FX
```

## 15. Organisation recommandée

Crée ces fonctions dans `BP_PlayerCharacter` :

```text
Attack
EnableSwordCollision
DisableSwordCollision
StartBlock
StopBlock
ApplyReceivedDamage
IsDamageFromFront
```

Cela évite un Event Graph trop désordonné.

## 16. Résultat attendu

Le joueur peut :

- Attaquer avec clic gauche
- Activer la collision de l’épée uniquement pendant le swing
- Toucher une cible une seule fois par attaque
- Bloquer avec clic droit
- Réduire ou annuler les dégâts si l’attaque vient de face
- Recevoir les dégâts complets si l’attaque vient de côté ou de dos
- Être ralenti pendant le blocage
- Ne pas attaquer pendant qu’il bloque

## 17. Problèmes fréquents

### L’animation d’attaque ne se joue pas

Vérifie que ton Animation Blueprint contient bien :

```text
State Machine → Slot DefaultSlot → Output Pose
```

### L’épée touche plusieurs fois

Vérifie que tu utilises bien :

```text
HitActors Contains OtherActor
```

et que tu fais :

```text
Clear HitActors
```

au début de chaque attaque.

### Le blocage marche même de dos

Vérifie le `Dot Product` dans `IsDamageFromFront`.

Valeur conseillée :

```text
Dot Product > 0.3
```

Pour un blocage plus strict :

```text
Dot Product > 0.6
```

### La collision de l’épée ne détecte rien

Vérifie :

```text
Generate Overlap Events = true
Collision Enabled = Query Only pendant l’attaque
La cible répond bien en Overlap au canal de l’épée
```

## 18. Version courte du flow Blueprint

```text
IA_Attack Started
→ If CanAttack && !IsBlocking
→ Play Attack Montage
→ Enable Sword Collision
→ Apply Damage on Overlap
→ Disable Sword Collision
```

```text
IA_Block Started
→ If !IsAttacking
→ IsBlocking = true
→ Slow Movement
→ Play Block Animation
```

```text
IA_Block Completed / Canceled
→ IsBlocking = false
→ Restore Movement
```

```text
Event AnyDamage
→ If IsBlocking && DamageFromFront
→ Damage *= BlockDamageRatio
→ Health -= Damage
```
