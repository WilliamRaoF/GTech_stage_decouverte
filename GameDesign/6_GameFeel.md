# 6. Le Game Feel

## Objectifs pédagogiques

À la fin de ce chapitre, vous serez capable de :

- Comprendre ce qu'est le Game Feel.
- Concevoir des contrôles agréables.
- Donner du poids aux actions du joueur.
- Utiliser les feedbacks visuels, sonores et physiques.
- Améliorer la sensation de contrôle.
- Comprendre pourquoi certains jeux paraissent immédiatement "satisfaisants".

---

# 6.1 Qu'est-ce que le Game Feel ?

Le **Game Feel** est l'ensemble des sensations ressenties lorsque le joueur interagit avec le jeu.

Il ne s'agit pas des graphismes.

Il ne s'agit pas du scénario.

Il s'agit de la **qualité des interactions**.

Deux jeux peuvent posséder exactement les mêmes mécaniques.

Pourtant :

- l'un paraît lourd,
- l'autre paraît fluide.

La différence vient du Game Feel.

Le joueur doit avoir l'impression que chaque action produit une réponse immédiate et satisfaisante.

---

# 6.2 Pourquoi le Game Feel est-il important ?

Les premières secondes déterminent souvent si le joueur poursuit l'expérience.

Si déplacer un personnage est agréable, le joueur accepte plus facilement :

- une histoire simple ;
- des graphismes modestes ;
- peu de contenu.

À l'inverse, des contrôles imprécis peuvent rendre un excellent concept frustrant.

On dit souvent :

> **Le joueur touche le gameplay avant de voir le contenu.**

---

# 6.3 Les composantes du Game Feel

Le Game Feel repose sur plusieurs éléments qui travaillent ensemble.

## Les contrôles

Le joueur doit avoir confiance dans les commandes.

Chaque action doit être :

- prévisible ;
- réactive ;
- cohérente.

---

## Les animations

Les animations donnent de la personnalité aux actions.

Exemple :

Un coup d'épée sans animation semble artificiel.

Avec une animation :

- préparation ;
- impact ;
- récupération,

l'action paraît crédible.

---

## Les effets visuels

Les particules renforcent les actions.

Exemples :

- poussière lors d'un saut ;
- étincelles lors d'un impact ;
- fumée après une explosion ;
- éclaboussures dans l'eau.

Ces effets rendent les interactions plus lisibles.

---

## Les effets sonores

Le son est souvent sous-estimé.

Chaque action importante devrait posséder son identité sonore.

Exemples :

- ramasser une pièce ;
- ouvrir un coffre ;
- toucher un ennemi ;
- réussir une parade.

Le joueur peut parfois comprendre une situation uniquement grâce au son.

---

## Les vibrations (Haptics)

Sur console et mobile, les vibrations améliorent les sensations.

Exemples :

- explosion ;
- collision ;
- tir ;
- réception après un saut.

Les vibrations doivent rester discrètes.

Une vibration permanente perd rapidement son intérêt.

---

# 6.4 Les principes fondamentaux

Le Game Feel repose sur plusieurs principes.

---

## Réactivité

Le délai entre l'action du joueur et la réaction du jeu doit être minimal.

Lorsque le joueur appuie sur un bouton :

↓

Le personnage agit immédiatement.

Un délai trop important donne une impression de lourdeur.

---

## Lisibilité

Le joueur doit comprendre ce qui vient de se produire.

Exemple :

Une attaque touche un ennemi.

Le jeu peut afficher :

- une animation ;
- un son ;
- une gerbe d'étincelles ;
- un nombre de dégâts ;
- un recul.

Tous ces éléments confirment la réussite de l'action.

---

## Cohérence

Les mêmes actions doivent toujours produire les mêmes résultats.

Si un saut fonctionne différemment sans raison apparente, le joueur perd confiance.

---

# 6.5 Le "Juice"

Le terme **Juice** désigne tous les petits effets qui rendent un jeu vivant.

Quelques exemples :

- caméra qui tremble légèrement ;
- particules ;
- effets de lumière ;
- sons variés ;
- ralentissement temporel ;
- rebond des objets ;
- animations secondaires.

Le Juice ne modifie pas les règles.

Il améliore uniquement la perception des actions.

---

# 6.6 Le Hit Stop

Le **Hit Stop** est une très courte pause lors d'un impact.

Durée typique :

Entre 30 et 100 millisecondes.

Effets :

- accentue la puissance ;
- améliore la lisibilité ;
- rend les combats plus satisfaisants.

Cette technique est largement utilisée dans les jeux de combat et les jeux d'action.

---

# 6.7 Le Screen Shake

Le **Screen Shake** consiste à faire vibrer brièvement la caméra.

Il est utilisé lors :

- d'une explosion ;
- d'un coup critique ;
- d'un saut puissant ;
- d'un boss.

Attention :

Un tremblement excessif fatigue le joueur.

Le dosage est essentiel.

---

# 6.8 Le Time Freeze

Le ralentissement du temps accentue certains événements.

Exemples :

- élimination d'un boss ;
- coup final ;
- esquive parfaite.

Une fraction de seconde suffit souvent à augmenter la tension dramatique.

---

# 6.9 Les animations

Une animation se décompose généralement en trois phases.

## Anticipation

Le personnage prépare son mouvement.

Exemple :

Lever l'épée avant de frapper.

---

## Action

Le mouvement principal.

Le joueur obtient le résultat attendu.

---

## Récupération

Le personnage revient dans sa position normale.

Cette phase évite que toutes les actions paraissent instantanées.

---

# 6.10 Les principes d'animation appliqués au jeu

Certaines règles de l'animation traditionnelle améliorent fortement le Game Feel.

## Anticipation

Préparer l'action.

---

## Follow Through

Les éléments continuent légèrement leur mouvement après l'action.

Exemple :

Une cape continue de flotter après l'arrêt du personnage.

---

## Overlapping Action

Les différentes parties du corps ne s'arrêtent pas simultanément.

Cela rend les mouvements naturels.

---

## Squash & Stretch

Déformer légèrement un objet lors d'un impact.

Exemple :

Une balle s'écrase légèrement avant de rebondir.

Cette technique augmente la sensation d'énergie.

---

# 6.11 Les contrôles

Les contrôles doivent être pensés avant tout pour le plaisir.

Quelques principes :

- accélération progressive ;
- freinage naturel ;
- vitesse cohérente ;
- inertie maîtrisée.

Chaque paramètre influence directement les sensations.

---

## Input Buffer

L'Input Buffer enregistre brièvement une commande effectuée juste avant qu'elle ne soit possible.

Exemple :

Le joueur appuie sur "Saut" quelques millisecondes avant d'atterrir.

Le personnage saute immédiatement lorsqu'il touche le sol.

Le jeu paraît plus réactif.

---

## Coyote Time

Le Coyote Time autorise un saut pendant un très court instant après avoir quitté une plateforme.

Sans cette aide :

Le joueur pense avoir sauté au bon moment…

…mais tombe.

Avec le Coyote Time :

Le saut réussit.

Le joueur a l'impression d'être précis.

En réalité, le jeu corrige légèrement son erreur.

---

# 6.12 Les récompenses sensorielles

Chaque réussite mérite une récompense perceptible.

Exemples :

Ramasser une pièce :

- son ;
- animation ;
- particules ;
- compteur qui augmente.

Le cerveau associe ces retours positifs à une récompense.

---

# 6.13 Les erreurs fréquentes

## Trop d'effets

Ajouter des particules partout réduit leur impact.

Le joueur ne remarque plus les événements importants.

---

## Aucun feedback

Si un ennemi reçoit un coup sans réagir, le joueur doute d'avoir touché sa cible.

Chaque interaction doit être confirmée.

---

## Contrôles imprécis

Un joueur accepte difficilement un échec causé par des commandes peu fiables.

Le contrôle doit toujours être plus précis que les compétences du joueur.

---

## Animations trop longues

Une animation spectaculaire mais lente peut rendre le personnage peu réactif.

Il faut trouver un équilibre entre esthétique et jouabilité.

---

# 6.14 Étude de cas : Hollow Knight

Pourquoi les combats de **Hollow Knight** sont-ils souvent cités comme référence ?

- contrôles très précis ;
- délais de réponse extrêmement faibles ;
- ennemis avec des animations lisibles ;
- impacts clairement signalés ;
- sons distinctifs ;
- légers reculs lors des coups.

Le joueur comprend immédiatement le résultat de chacune de ses actions.

---

# 6.15 Étude de cas : Celeste

Le déplacement de **Celeste** est réputé pour son excellence.

Pourquoi ?

- accélération rapide ;
- Coyote Time ;
- Input Buffer ;
- contrôles constants ;
- physique prévisible.

Le jeu aide discrètement le joueur sans donner l'impression de tricher.

C'est un excellent exemple de Game Feel invisible.

---

# 6.16 Le Game Feel et le prototypage

Le Game Feel doit être testé très tôt.

Même avec :

- des cubes ;
- des capsules ;
- des sons temporaires,

il est possible d'évaluer :

- les déplacements ;
- les sauts ;
- les combats ;
- les sensations générales.

Un prototype amusant avec des graphismes simples est souvent plus prometteur qu'un jeu magnifique mais désagréable à jouer.

---

# Exercices

## Exercice 1

Prenez un personnage de votre jeu.

Listez toutes ses actions.

Pour chacune, définissez :

- l'animation ;
- le son ;
- les particules ;
- les vibrations ;
- le feedback visuel.

---

## Exercice 2

Analysez un jeu d'action.

Repérez :

- les Hit Stops ;
- les Screen Shakes ;
- les ralentissements temporels.

Comment influencent-ils votre perception des impacts ?

---

## Exercice 3

Créez un prototype de déplacement.

Testez :

- différentes vitesses ;
- différentes hauteurs de saut ;
- différentes accélérations.

Notez les sensations obtenues.

---

# À retenir

- Le Game Feel est la qualité des sensations produites par les interactions.
- Les contrôles doivent être réactifs, cohérents et précis.
- Les feedbacks visuels, sonores et haptiques renforcent les actions.
- Des techniques comme le Hit Stop, le Coyote Time et l'Input Buffer améliorent fortement l'expérience.
- Le Juice donne de la personnalité au jeu sans modifier ses règles.
- Le Game Feel se travaille dès les premiers prototypes et se peaufine tout au long du développement.

---

# Chapitre suivant

Dans le chapitre 7, nous aborderons **l'équilibrage (Game Balance)** : comment ajuster la difficulté, les statistiques, les ressources, les ennemis et les récompenses afin de créer une expérience juste, stimulante et durable.
