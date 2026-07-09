# Tutoriel UE 5.6 Blueprint – Courir, Wall Jump et Grappin

## Objectif

Dans ce tutoriel, nous allons ajouter trois mécaniques de déplacement à un personnage Unreal Engine 5.6 en Blueprint :

- courir / sprinter ;
- faire un wall jump ;
- utiliser un grappin.

Le tutoriel part du principe que tu as déjà un personnage jouable de type **Character**, par exemple :

```
BP_Player
```

et que ce personnage possède un composant :

```
CharacterMovement
```

---

# Partie 1 – Ajouter la course

## Objectif

Quand le joueur maintient une touche, le personnage court plus vite. Quand il relâche la touche, il revient à sa vitesse normale.

---

## Étape 1 – Créer les variables

Dans `BP_Player`, crée deux variables :

```
WalkSpeed
```

Type :

```
Float
```

Valeur :

```
500
```

Puis :

```
RunSpeed
```

Type :

```
Float
```

Valeur :

```
900
```

Ces deux variables permettent de régler facilement la vitesse normale et la vitesse de course.

---

## Étape 2 – Régler la vitesse normale au lancement

Dans l'Event Graph :

```
Event BeginPlay
    ↓
CharacterMovement
    ↓
Set Max Walk Speed
```

Valeur :

```
WalkSpeed
```

Comme ça, au lancement du jeu, le personnage utilise toujours la vitesse normale.

---

## Étape 3 – Créer l'action de course

Dans le système d'input de ton projet, crée une action :

```
Sprint
```

Associe-la à une touche, par exemple :

```
Left Shift
```

---

## Étape 4 – Courir quand la touche est maintenue

Dans `BP_Player`, ajoute l'événement :

```
Input Action Sprint
```

Sur **Pressed** :

```
CharacterMovement
    ↓
Set Max Walk Speed
```

Valeur :

```
RunSpeed
```

Sur **Released** :

```
CharacterMovement
    ↓
Set Max Walk Speed
```

Valeur :

```
WalkSpeed
```

---

## Résultat

Quand le joueur maintient **Shift**, le personnage court.

Quand il relâche **Shift**, il marche normalement.

---

# Partie 2 – Ajouter le Wall Jump

## Objectif

Le personnage peut sauter contre un mur s'il est en l'air et proche d'une surface.

Le wall jump va :

- détecter un mur devant le joueur ;
- vérifier que le joueur n'est pas au sol ;
- appliquer une impulsion vers le haut et vers l'extérieur du mur.

---

## Étape 1 – Créer les variables

Dans `BP_Player`, crée les variables suivantes :

```
WallJumpForwardDistance
```

Type :

```
Float
```

Valeur :

```
80
```

Cette variable définit la distance de détection du mur.

---

```
WallJumpUpForce
```

Type :

```
Float
```

Valeur :

```
700
```

Cette variable définit la force verticale du saut.

---

```
WallJumpPushForce
```

Type :

```
Float
```

Valeur :

```
600
```

Cette variable définit la force qui pousse le joueur loin du mur.

---

```
CanWallJump
```

Type :

```
Boolean
```

Valeur :

```
False
```

Cette variable indique si le joueur est actuellement proche d'un mur.

---

```
WallNormal
```

Type :

```
Vector
```

Cette variable stockera la direction opposée au mur.

---

## Étape 2 – Détecter un mur avec un Line Trace

Dans l'Event Graph, utilise :

```
Event Tick
```

Depuis le personnage :

```
Get Actor Location
```

Puis :

```
Get Actor Forward Vector
```

Multiplie le Forward Vector par :

```
WallJumpForwardDistance
```

Puis ajoute ce résultat à la position du personnage.

Schéma logique :

```
Start = Actor Location
End = Actor Location + Actor Forward Vector × WallJumpForwardDistance
```

Ajoute ensuite :

```
Line Trace By Channel
```

Réglages :

```
Trace Channel = Visibility
Draw Debug Type = For Duration
```

Le mode debug permet de voir le rayon dans le niveau pendant les tests.

---

## Étape 3 – Vérifier que le joueur est en l'air

Après le `Line Trace By Channel`, récupère :

```
Break Hit Result
```

Puis vérifie aussi si le joueur tombe :

```
CharacterMovement
    ↓
Is Falling
```

Ensuite, utilise une condition :

```
Branch
```

Condition :

```
Line Trace Hit = True
AND
Is Falling = True
```

Si la condition est vraie :

```
Set CanWallJump = True
Set WallNormal = Hit Normal
```

Si elle est fausse :

```
Set CanWallJump = False
```

---

## Étape 4 – Modifier l'action de saut

Dans l'événement de saut du personnage :

```
Input Action Jump
```

ou :

```
IA_Jump
```

selon ton système d'input.

Avant d'appeler le saut normal, ajoute :

```
Branch (CanWallJump)
```

### Si CanWallJump est False

Laisse le saut normal :

```
Jump
```

### Si CanWallJump est True

On applique un wall jump.

Utilise :

```
Launch Character
```

Pour créer le vecteur de lancement :

```
WallNormal × WallJumpPushForce
```

Puis ajoute :

```
Vector Z = WallJumpUpForce
```

Le résultat doit ressembler à ceci :

```
Launch Velocity =
    X/Y = WallNormal × WallJumpPushForce
    Z = WallJumpUpForce
```

Réglages du nœud `Launch Character` :

```
XY Override = True
Z Override = True
```

---

## Étape 5 – Éviter les wall jumps infinis

Après le `Launch Character`, ajoute :

```
Set CanWallJump = False
```

Tu peux aussi ajouter un petit délai :

```
Delay = 0.2
```

avant de permettre un nouveau wall jump, si le joueur peut spammer trop facilement.

---

## Résultat

Le joueur peut maintenant sauter contre un mur.

Quand il est en l'air et proche d'un mur, appuyer sur saut l'expulse vers l'extérieur du mur avec une impulsion verticale.

---

# Partie 3 – Ajouter un grappin

## Objectif

Le joueur vise un point avec la caméra, appuie sur une touche, et est tiré vers le point touché.

Le grappin va :

- envoyer un Line Trace depuis la caméra ;
- vérifier qu'un objet est touché ;
- stocker le point d'accroche ;
- tirer le joueur vers ce point tant que le grappin est actif.

---

## Étape 1 – Créer les variables

Dans `BP_Player`, crée :

```
GrappleDistance
```

Type :

```
Float
```

Valeur :

```
3000
```

Distance maximale du grappin.

---

```
GrappleSpeed
```

Type :

```
Float
```

Valeur :

```
3500
```

Vitesse à laquelle le joueur est tiré.

---

```
IsGrappling
```

Type :

```
Boolean
```

Valeur :

```
False
```

Indique si le grappin est actif.

---

```
GrapplePoint
```

Type :

```
Vector
```

Stocke la position touchée par le grappin.

---

```
StopGrappleDistance
```

Type :

```
Float
```

Valeur :

```
150
```

Distance à partir de laquelle le grappin s'arrête automatiquement.

---

## Étape 2 – Créer l'action du grappin

Dans les inputs, crée une action :

```
Grapple
```

Associe-la à une touche, par exemple :

```
E
```

ou au clic droit de la souris.

---

## Étape 3 – Lancer un Line Trace depuis la caméra

Dans `BP_Player`, ajoute :

```
Input Action Grapple
```

Sur **Pressed**, crée un Line Trace.

Si ton personnage possède une caméra nommée `FollowCamera`, fais :

```
FollowCamera
    ↓
Get World Location
```

Ce sera le point de départ :

```
Start
```

Puis :

```
FollowCamera
    ↓
Get Forward Vector
```

Multiplie ce vecteur par :

```
GrappleDistance
```

Ajoute-le à la position de la caméra :

```
End = Camera Location + Camera Forward Vector × GrappleDistance
```

Utilise ensuite :

```
Line Trace By Channel
```

Réglages :

```
Trace Channel = Visibility
Draw Debug Type = For Duration
```

---

## Étape 4 – Activer le grappin si le trace touche quelque chose

Depuis le `Line Trace By Channel` :

```
Branch
```

Condition :

```
Return Value
```

Si c'est vrai :

```
Break Hit Result
    ↓
Impact Point
```

Puis :

```
Set GrapplePoint = Impact Point
Set IsGrappling = True
```

Le point touché devient le point d'accroche du grappin.

---

## Étape 5 – Tirer le joueur vers le point

Dans l'Event Graph :

```
Event Tick
    ↓
Branch (IsGrappling)
```

Si `IsGrappling` est vrai :

1. Récupère la position du joueur :

```
Get Actor Location
```

2. Calcule la direction vers le point :

```
GrapplePoint - Actor Location
```

3. Normalise ce vecteur :

```
Normalize
```

4. Multiplie-le par :

```
GrappleSpeed
```

5. Applique la vélocité avec :

```
Launch Character
```

Réglages :

```
Launch Velocity = Direction × GrappleSpeed
XY Override = True
Z Override = True
```

---

## Étape 6 – Arrêter le grappin automatiquement

Toujours dans le `Tick`, calcule la distance entre le joueur et le point :

```
Distance
```

Avec :

```
Vector Distance
```

Entre :

```
Actor Location
GrapplePoint
```

Ajoute un `Branch` :

```
Distance < StopGrappleDistance
```

Si vrai :

```
Set IsGrappling = False
```

Le grappin s'arrête quand le joueur arrive près du point.

---

## Étape 7 – Arrêter le grappin quand la touche est relâchée

Sur l'action :

```
Input Action Grapple
```

Sur **Released** :

```
Set IsGrappling = False
```

Le joueur peut donc relâcher la touche pour arrêter le grappin.

---

## Résultat

Le joueur peut viser un mur, un plafond ou une plateforme, appuyer sur la touche du grappin, puis être attiré vers le point touché.

---

# Partie 4 – Résumé des touches

| Action | Touche conseillée |
|---|---|
| Courir | Left Shift |
| Sauter | Space |
| Wall Jump | Space près d'un mur |
| Grappin | E ou clic droit |

---

# Partie 5 – Conseils de réglage

## Pour la course

Si le joueur va trop vite :

```
RunSpeed = 750
```

Si le joueur est trop lent :

```
RunSpeed = 1000
```

---

## Pour le wall jump

Si le joueur ne monte pas assez :

```
WallJumpUpForce = 850
```

Si le joueur n'est pas assez repoussé du mur :

```
WallJumpPushForce = 800
```

Si le mur n'est pas détecté :

```
WallJumpForwardDistance = 120
```

---

## Pour le grappin

Si le grappin est trop lent :

```
GrappleSpeed = 4500
```

Si le grappin est trop brutal :

```
GrappleSpeed = 2500
```

Si le joueur s'arrête trop loin du point :

```
StopGrappleDistance = 80
```

Si le joueur peut attraper des objets trop éloignés :

```
GrappleDistance = 2000
```

---

# Partie 6 – Version simple du fonctionnement

## Courir

```
Shift Pressed
    ↓
Set Max Walk Speed = RunSpeed

Shift Released
    ↓
Set Max Walk Speed = WalkSpeed
```

## Wall Jump

```
Event Tick
    ↓
Line Trace devant le joueur
    ↓
Si mur touché + joueur en l'air
    ↓
CanWallJump = True
```

```
Jump Pressed
    ↓
Si CanWallJump = True
    ↓
Launch Character vers l'extérieur du mur + vers le haut
```

## Grappin

```
Grapple Pressed
    ↓
Line Trace depuis la caméra
    ↓
Si quelque chose est touché
    ↓
Stocker GrapplePoint
    ↓
IsGrappling = True
```

```
Event Tick
    ↓
Si IsGrappling = True
    ↓
Direction = GrapplePoint - Actor Location
    ↓
Launch Character vers GrapplePoint
```

---

# Conclusion

Tu as maintenant trois mécaniques de déplacement en Blueprint :

- la course ;
- le wall jump ;
- le grappin.

Elles peuvent être utilisées séparément ou ensemble pour créer un gameplay plus nerveux, proche d'un jeu de parkour ou d'action.
