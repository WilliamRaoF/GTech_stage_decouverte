# UE 5.6 Blueprint — Respiration obligatoire, fermeture des yeux et textes déclenchés par zones

Ce tutoriel explique comment créer trois mécaniques en Blueprint dans Unreal Engine 5.6 :

1. Le joueur doit appuyer régulièrement sur une touche pour respirer.
2. S’il ne respire pas à temps, il meurt.
3. Le joueur peut fermer les yeux avec une touche.
4. Des textes apparaissent quand le joueur entre dans des zones définies.

Le tutoriel est pensé pour un projet en First Person ou Third Person Blueprint.

---

## 1. Préparer les inputs

Avec Enhanced Input, crée trois actions :

| Input Action | Type | Utilisation |
|---|---|---|
| `IA_Breathe` | Digital / Bool | Respirer |
| `IA_CloseEyes` | Digital / Bool | Fermer les yeux |
| `IA_Interact` | Digital / Bool | Optionnel, pour valider un texte |

Dans ton `Input Mapping Context`, ajoute par exemple :

| Touche | Action |
|---|---|
| `R` ou `Space` | `IA_Breathe` |
| `Left Ctrl` ou `E` | `IA_CloseEyes` |

---

## 2. Variables à créer dans le Blueprint du joueur

Dans ton `BP_PlayerCharacter`, crée ces variables :

| Variable | Type | Valeur par défaut | Rôle |
|---|---:|---:|---|
| `BreathAmount` | Float | `100` | Niveau d’air actuel |
| `MaxBreath` | Float | `100` | Air maximum |
| `BreathDrainRate` | Float | `12` | Air perdu par seconde |
| `BreathGainAmount` | Float | `35` | Air gagné quand le joueur respire |
| `bIsDead` | Boolean | `False` | Bloque les actions après la mort |
| `bEyesClosed` | Boolean | `False` | Indique si les yeux sont fermés |
| `EyeCloseFadeSpeed` | Float | `5` | Vitesse du fondu noir |

---

## 3. Créer la respiration obligatoire

Dans `BP_PlayerCharacter`, utilise l’événement `Event Tick`.

### Logique Blueprint

```text
Event Tick
→ Branch : bIsDead == false
    → BreathAmount = BreathAmount - BreathDrainRate * Delta Seconds
    → Clamp BreathAmount entre 0 et MaxBreath
    → Branch : BreathAmount <= 0
        → True : Die()
```

### Fonction `Die`

Crée une fonction `Die` dans le joueur.

```text
Die
→ Set bIsDead = true
→ Disable Input
→ Play Animation / Ragdoll / Game Over Widget
→ Print String : "Vous avez oublié de respirer."
```

Tu peux aussi appeler un écran de Game Over :

```text
Create Widget WBP_GameOver
→ Add to Viewport
→ Set Game Paused true
```

---

## 4. Appuyer sur une touche pour respirer

Dans le `BP_PlayerCharacter`, ajoute l’événement de ton input :

```text
IA_Breathe Started
→ Branch : bIsDead == false
    → BreathAmount = BreathAmount + BreathGainAmount
    → Clamp BreathAmount entre 0 et MaxBreath
    → Play Sound : souffle / respiration
    → Optionnel : jouer une animation courte de respiration
```

Exemple :

```text
IA_Breathe Started
→ Set BreathAmount = Clamp(BreathAmount + BreathGainAmount, 0, MaxBreath)
```

---

## 5. Afficher une jauge de respiration

Crée un widget `WBP_PlayerHUD`.

Ajoute une `Progress Bar` nommée `PB_Breath`.

Dans le widget, crée une variable :

| Variable | Type |
|---|---|
| `PlayerRef` | `BP_PlayerCharacter` Object Reference |

Dans le `Event Construct` du widget :

```text
Get Player Character
→ Cast to BP_PlayerCharacter
→ Set PlayerRef
```

Pour la valeur de la Progress Bar :

```text
PB_Breath Percent = PlayerRef.BreathAmount / PlayerRef.MaxBreath
```

Tu peux aussi changer la couleur quand l’air est bas :

```text
Si BreathAmount < 25
→ couleur rouge
Sinon
→ couleur normale
```

---

## 6. Fermer les yeux avec une touche

Le plus simple est d’utiliser un widget noir qui couvre tout l’écran.

### Créer le widget `WBP_EyesOverlay`

Dans UMG :

1. Crée un widget `WBP_EyesOverlay`.
2. Ajoute une `Image` plein écran.
3. Mets la couleur en noir.
4. Mets son opacité à `0` au début.
5. Nomme l’image `IMG_BlackScreen`.

Dans `BP_PlayerCharacter`, crée une variable :

| Variable | Type |
|---|---|
| `EyesOverlayRef` | `WBP_EyesOverlay` Object Reference |

Au `Begin Play` du joueur :

```text
Create Widget WBP_EyesOverlay
→ Set EyesOverlayRef
→ Add to Viewport
```

---

## 7. Input pour fermer / ouvrir les yeux

Avec l’action `IA_CloseEyes` :

```text
IA_CloseEyes Started
→ Set bEyesClosed = true

IA_CloseEyes Completed
→ Set bEyesClosed = false
```

Ensuite, dans `Event Tick`, ajoute :

```text
Branch : bEyesClosed
→ True : CurrentOpacity va vers 1
→ False : CurrentOpacity va vers 0
```

Blueprint conseillé :

```text
Event Tick
→ Get IMG_BlackScreen Render Opacity
→ FInterp To
    Current = opacité actuelle
    Target = 1 si bEyesClosed, sinon 0
    Delta Time = Delta Seconds
    Interp Speed = EyeCloseFadeSpeed
→ Set Render Opacity
```

Résultat :

- Si le joueur maintient la touche, l’écran devient noir.
- Quand il relâche, la vision revient doucement.

---

## 8. Variante : les yeux fermés ralentissent le joueur

Optionnel, mais utile pour une mécanique d’horreur ou de tension.

```text
IA_CloseEyes Started
→ Set bEyesClosed = true
→ Character Movement Max Walk Speed = 150

IA_CloseEyes Completed
→ Set bEyesClosed = false
→ Character Movement Max Walk Speed = 500
```

---

## 9. Créer un système de texte déclenché par zones

Nous allons créer un Blueprint réutilisable : `BP_TextTriggerZone`.

### Composants du Blueprint

Dans `BP_TextTriggerZone`, ajoute :

| Composant | Rôle |
|---|---|
| `Box Collision` | Zone de déclenchement |
| `Billboard` | Optionnel, pour voir la zone dans l’éditeur |

---

## 10. Variables de `BP_TextTriggerZone`

Crée ces variables :

| Variable | Type | Instance Editable | Rôle |
|---|---|---|---|
| `TextToShow` | Text | Oui | Texte affiché |
| `DisplayTime` | Float | Oui | Durée d’affichage |
| `bTriggerOnlyOnce` | Boolean | Oui | Une seule activation |
| `bHasTriggered` | Boolean | Non | Empêche de relancer |

Valeurs conseillées :

```text
TextToShow = "Je dois continuer à respirer..."
DisplayTime = 4.0
bTriggerOnlyOnce = true
```

---

## 11. Widget pour afficher les textes

Crée un widget `WBP_ScreenText`.

Ajoute :

| Élément | Nom |
|---|---|
| Text Block | `TXT_Message` |

Dans le widget, crée une fonction `SetMessage` :

```text
Input : NewMessage de type Text
→ Set Text de TXT_Message = NewMessage
```

Optionnel : ajoute une animation UMG `FadeInOut`.

---

## 12. Créer une fonction d’affichage dans le joueur

Dans `BP_PlayerCharacter`, crée une variable :

| Variable | Type |
|---|---|
| `ScreenTextRef` | `WBP_ScreenText` Object Reference |

Au `Begin Play` :

```text
Create Widget WBP_ScreenText
→ Set ScreenTextRef
→ Add to Viewport
→ Set Visibility Hidden
```

Crée une fonction dans le joueur : `ShowScreenText`.

Entrées :

| Nom | Type |
|---|---|
| `Message` | Text |
| `Duration` | Float |

Blueprint :

```text
ShowScreenText(Message, Duration)
→ Set Visibility Visible
→ ScreenTextRef.SetMessage(Message)
→ Clear and Invalidate Timer by Handle, si tu utilises un timer
→ Set Timer by Event
    Time = Duration
    Event : HideScreenText
```

Crée aussi la fonction `HideScreenText` :

```text
HideScreenText
→ Set Visibility Hidden
```

---

## 13. Déclencher le texte avec la zone

Dans `BP_TextTriggerZone`, sélectionne `Box Collision`.

Ajoute l’événement :

```text
On Component Begin Overlap
```

Logique :

```text
On Component Begin Overlap
→ Cast Other Actor to BP_PlayerCharacter
→ Branch : Cast réussi
    → Branch : bTriggerOnlyOnce == false OR bHasTriggered == false
        → Set bHasTriggered = true
        → Call ShowScreenText sur le joueur
            Message = TextToShow
            Duration = DisplayTime
```

En pseudo Blueprint :

```text
Begin Overlap
→ Other Actor
→ Cast to BP_PlayerCharacter
→ Branch : Is Valid
    → Branch : Can Trigger
        → Set bHasTriggered = true
        → Player.ShowScreenText(TextToShow, DisplayTime)
```

---

## 14. Placer les zones dans le niveau

Dans ton niveau :

1. Glisse `BP_TextTriggerZone` dans la scène.
2. Redimensionne la `Box Collision`.
3. Dans le panneau Details, modifie `TextToShow`.
4. Modifie `DisplayTime`.
5. Coche ou décoche `bTriggerOnlyOnce`.

Exemples de textes :

```text
"N’oublie pas de respirer."
"Quelque chose bouge quand je ferme les yeux..."
"La porte semble réagir à ma respiration."
"Je ne dois pas paniquer. Inspire. Expire."
```

---

## 15. Ajouter une tension quand le joueur manque d’air

Tu peux ajouter des effets quand `BreathAmount` descend trop bas.

Dans `Event Tick` du joueur :

```text
Si BreathAmount < 30
→ Jouer son de battement de cœur
→ Ajouter vignette rouge/noire
→ Tremblement caméra léger
```

Exemple simple :

```text
Branch : BreathAmount < 30
→ Start Camera Shake
```

Attention : évite de relancer le son ou le camera shake à chaque Tick. Utilise un booléen :

| Variable | Type |
|---|---|
| `bLowBreathWarningActive` | Boolean |

```text
Si BreathAmount < 30 ET bLowBreathWarningActive == false
→ Set bLowBreathWarningActive = true
→ Activer les effets

Si BreathAmount >= 30 ET bLowBreathWarningActive == true
→ Set bLowBreathWarningActive = false
→ Désactiver les effets
```

---

## 16. Résumé des Blueprints à créer

| Blueprint / Widget | Rôle |
|---|---|
| `BP_PlayerCharacter` | Gère respiration, mort, yeux fermés, textes |
| `WBP_PlayerHUD` | Affiche la jauge de respiration |
| `WBP_EyesOverlay` | Écran noir quand les yeux sont fermés |
| `WBP_ScreenText` | Affiche les textes scénarisés |
| `BP_TextTriggerZone` | Zone qui déclenche un texte |

---

## 17. Ordre conseillé de création

1. Créer les Input Actions.
2. Ajouter les variables de respiration dans le joueur.
3. Faire baisser `BreathAmount` avec `Event Tick`.
4. Ajouter `IA_Breathe` pour remonter l’air.
5. Ajouter la mort quand `BreathAmount <= 0`.
6. Créer le HUD de respiration.
7. Créer le widget noir pour les yeux.
8. Ajouter `IA_CloseEyes`.
9. Créer le widget de texte.
10. Créer `BP_TextTriggerZone`.
11. Placer les zones dans le niveau.

---

## 18. Améliorations possibles

- Obliger le joueur à respirer en rythme, pas juste spammer une touche.
- Ajouter une respiration sonore plus forte quand l’air est bas.
- Faire apparaître certains ennemis uniquement quand les yeux sont fermés.
- Afficher des textes différents selon l’état du joueur.
- Déclencher des événements si le joueur ferme les yeux dans une zone précise.
- Faire perdre plus vite l’air quand le joueur court.

Exemple :

```text
Si le joueur court
→ BreathDrainRate = 25
Sinon
→ BreathDrainRate = 12
```

---

## 19. Exemple de gameplay complet

```text
Le joueur avance dans un couloir.
Une zone affiche : "Respire. Ne panique pas."
La jauge d’air descend.
Le joueur appuie sur R pour respirer.
Plus loin, une autre zone affiche : "Ferme les yeux."
Le joueur maintient E.
L’écran devient noir.
Un son se déclenche.
Quand il rouvre les yeux, un objet a changé de place.
S’il oublie de respirer, la jauge tombe à 0 et le Game Over apparaît.
```

---

## 20. Version simple de la logique principale

```text
Event Tick
→ Si bIsDead == false
    → BreathAmount -= BreathDrainRate * DeltaSeconds
    → BreathAmount = Clamp(BreathAmount, 0, MaxBreath)
    → Si BreathAmount <= 0
        → Die()

IA_Breathe Started
→ Si bIsDead == false
    → BreathAmount += BreathGainAmount
    → BreathAmount = Clamp(BreathAmount, 0, MaxBreath)

IA_CloseEyes Started
→ bEyesClosed = true

IA_CloseEyes Completed
→ bEyesClosed = false

BP_TextTriggerZone BeginOverlap
→ Cast vers BP_PlayerCharacter
→ Player.ShowScreenText(TextToShow, DisplayTime)
```
