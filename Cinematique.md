# Tutoriel UE 5.6 Blueprint -- Caméra travelling au lancement du jeu

## Objectif

Dans ce tutoriel, nous allons créer une caméra qui se déplace
automatiquement le long d'un chemin défini dès que le joueur lance le
jeu.

Le résultat sera le suivant :

-   Le jeu démarre.
-   La caméra devient la vue principale.
-   La caméra suit un chemin que tu as dessiné dans le niveau.
-   La caméra regarde dans la direction du chemin pendant tout le
    travelling.

------------------------------------------------------------------------

# Étape 1 -- Créer le Blueprint

Dans le **Content Browser** :

1.  Clique sur **Add**.
2.  Choisis **Blueprint Class**.
3.  Sélectionne **Actor**.
4.  Nomme-le :

```{=html}
<!-- -->
```
    BP_CameraTravelling

Double-clique dessus pour l'ouvrir.

------------------------------------------------------------------------

# Étape 2 -- Ajouter les composants

Dans le Blueprint, ajoute les composants suivants :

## 1. Spline

Clique sur **Add Component** puis ajoute :

    Spline

Renomme-la si besoin :

    TravelSpline

La Spline servira à dessiner le trajet de la caméra directement dans le
niveau.

## 2. Camera

Ajoute ensuite :

    Camera

Fais glisser la Camera sous la Spline dans la hiérarchie si tu souhaites
qu'elle en soit enfant.

Aucun réglage particulier n'est nécessaire pour commencer.

------------------------------------------------------------------------

# Étape 3 -- Placer le Blueprint dans le niveau

Compile puis sauvegarde le Blueprint.

Glisse **BP_CameraTravelling** dans ta scène.

Sélectionne-le dans le niveau.

Tu verras apparaître les points de la Spline.

Déplace ces points pour créer ton trajet :

-   départ devant l'entrée
-   passage dans un couloir
-   vue sur une salle
-   arrêt devant le bâtiment principal

Tu peux ajouter de nouveaux points avec **Alt + Glisser** sur un point
existant.

Prends le temps de créer une belle trajectoire, car c'est elle que la
caméra suivra.

------------------------------------------------------------------------

# Étape 4 -- Créer les variables

Ajoute une variable :

## Duration

Type :

    Float

Valeur :

    20.0

Cette variable représente la durée totale du travelling en secondes.

------------------------------------------------------------------------

# Étape 5 -- Créer la Timeline

Dans l'Event Graph :

1.  Clic droit.
2.  Tape :

```{=html}
<!-- -->
```
    Add Timeline

Nomme-la :

    TL_Travelling

Ouvre-la.

Ajoute une **Float Track** appelée :

    Alpha

Configure-la ainsi :

-   Temps 0 → Valeur 0
-   Temps = Duration (ou 20 si tu commences) → Valeur 1

Laisse l'interpolation en **Auto** pour obtenir un mouvement fluide.

La Timeline produira une valeur comprise entre **0 et 1** pendant toute
la durée du travelling.

------------------------------------------------------------------------

# Étape 6 -- Donner la caméra au joueur

Dans l'Event Graph :

    Event BeginPlay
        ↓
    Get Player Controller
        ↓
    Set View Target with Blend

Réglages :

-   New View Target = Self
-   Blend Time = 0

Ainsi, au lancement du jeu, le joueur regardera immédiatement à travers
cette caméra.

Puis relie l'exécution au nœud :

    Play (TL_Travelling)

La Timeline démarrera dès le BeginPlay.

------------------------------------------------------------------------

# Étape 7 -- Faire avancer la caméra

Sur la sortie **Update** de la Timeline :

1.  Récupère la longueur de la Spline :

```{=html}
<!-- -->
```
    Get Spline Length

2.  Multiplie cette longueur par la valeur **Alpha**.

```{=html}
<!-- -->
```
    Spline Length × Alpha

Le résultat correspond à la distance parcourue sur la Spline.

3.  Branche cette distance sur :

```{=html}
<!-- -->
```
    Get Location at Distance Along Spline

Coordinate Space :

    World

4.  Branche ensuite la position obtenue sur :

```{=html}
<!-- -->
```
    Set World Location

Target :

    Camera

À chaque image, la caméra se déplacera un peu plus loin sur la Spline.

------------------------------------------------------------------------

# Étape 8 -- Faire tourner la caméra

Toujours depuis la même distance :

    Get Rotation at Distance Along Spline

Coordinate Space :

    World

Relie la sortie à :

    Set World Rotation

Target :

    Camera

La caméra regardera automatiquement dans la direction du chemin.

------------------------------------------------------------------------

# Étape 9 -- Tester

Compile le Blueprint.

Sauvegarde.

Lance le jeu.

Si tout est correctement branché :

-   la caméra devient la vue du joueur ;
-   elle suit la Spline du début à la fin ;
-   elle tourne automatiquement dans la direction du trajet ;
-   le déplacement dure le nombre de secondes défini dans **Duration**.

------------------------------------------------------------------------

# Conseils

-   Utilise des courbes sur les points de la Spline pour éviter les
    virages brusques.
-   Augmente **Duration** pour ralentir le travelling.
-   Diminue **Duration** pour accélérer le déplacement.
-   Déplace simplement les points de la Spline pour modifier le parcours
    sans toucher au Blueprint.
