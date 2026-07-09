# Tutoriel UE 5.6 Blueprint -- Modifier la gravité

## Objectif

Dans ce tutoriel, nous allons apprendre à modifier la gravité d'un
personnage en Blueprint.

> **Important :**
>
> Dans Unreal Engine, il n'existe pas de nœud Blueprint permettant de
> modifier directement la gravité globale du monde pendant l'exécution.
> En revanche, chaque personnage possède un **Character Movement
> Component** qui permet de modifier le multiplicateur de gravité
> appliqué au personnage.

------------------------------------------------------------------------

# Étape 1 -- Ouvrir le Blueprint du personnage

Dans le **Content Browser** :

1.  Ouvre le Blueprint de ton personnage (par exemple `BP_Player`).
2.  Vérifie qu'il hérite bien de **Character**.

------------------------------------------------------------------------

# Étape 2 -- Sélectionner le Character Movement

Dans le panneau **Components** :

-   sélectionne **CharacterMovement**.

C'est ce composant qui gère :

-   les déplacements ;
-   les sauts ;
-   la gravité.

------------------------------------------------------------------------

# Étape 3 -- Comprendre Gravity Scale

Le paramètre **Gravity Scale** multiplie la gravité.

Valeurs courantes :

    Valeur Effet
  -------- ---------------------------
         0 Aucune gravité
       0.5 Gravité réduite de moitié
         1 Gravité normale
         2 Deux fois plus forte
         5 Gravité très forte

------------------------------------------------------------------------

# Étape 4 -- Modifier la gravité au lancement du jeu

Dans l'Event Graph :

    Event BeginPlay
        ↓
    Character Movement
        ↓
    Set Gravity Scale

Renseigne par exemple :

    Gravity Scale = 2

Au lancement du jeu, le personnage sera deux fois plus lourd.

------------------------------------------------------------------------

# Étape 5 -- Changer la gravité avec une touche

Dans **Project Settings \> Input**, crée une action nommée :

    ChangeGravity

Associe-la par exemple à la touche **G**.

Dans le Blueprint :

    Input Action ChangeGravity
            ↓
    Set Gravity Scale

Tu peux mettre :

    0.3

Le personnage flottera davantage.

------------------------------------------------------------------------

# Étape 6 -- Alterner entre deux gravités

Crée une variable :

    HeavyGravity

Type :

    Boolean

Dans l'Event Graph :

    Input Action ChangeGravity
            ↓
    Branch

Si `HeavyGravity` est **False** :

    Set Gravity Scale = 3
    Set HeavyGravity = True

Sinon :

    Set Gravity Scale = 1
    Set HeavyGravity = False

À chaque pression sur **G**, la gravité bascule entre normale et forte.

------------------------------------------------------------------------

# Étape 7 -- Désactiver complètement la gravité

Utilise simplement :

    Set Gravity Scale = 0

Le personnage ne tombera plus.

Si tu souhaites qu'il se déplace librement dans toutes les directions,
change également le **Movement Mode** :

    Set Movement Mode

Valeur :

    Flying

Ainsi, le personnage pourra voler sans être affecté par la gravité.

------------------------------------------------------------------------

# Conseils

-   Évite des valeurs supérieures à 10, qui rendent les mouvements très
    brusques.
-   Après avoir changé la gravité, teste les paramètres de saut
    (`Jump Z Velocity`) pour conserver un gameplay agréable.
-   Pour créer une zone à faible gravité, appelle `Set Gravity Scale`
    lorsque le joueur entre dans un `Box Collision`, puis remets la
    valeur à `1` lorsqu'il en sort.
