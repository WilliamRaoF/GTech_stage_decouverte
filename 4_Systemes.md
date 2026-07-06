# 4. Les systèmes de jeu

## Objectifs pédagogiques

À la fin de ce chapitre, vous serez capable de :

- Comprendre ce qu'est un système de jeu.
- Concevoir des systèmes interconnectés.
- Différencier les systèmes fermés et ouverts.
- Utiliser les boucles de rétroaction (feedback loops).
- Concevoir une économie simple.
- Éviter les systèmes déséquilibrés.
- Penser un jeu comme un ensemble de règles qui interagissent.

---

# 4.1 Qu'est-ce qu'un système de jeu ?

Un **système de jeu** est un ensemble de règles et de mécaniques qui interagissent entre elles pour produire des comportements.

Une mécanique décrit une action.

Un système décrit un ensemble d'actions reliées.

Exemple :

Dans un RPG :

- les ennemis donnent de l'expérience ;
- l'expérience fait monter de niveau ;
- monter de niveau augmente les statistiques ;
- de meilleures statistiques permettent d'affronter des ennemis plus puissants ;
- ces ennemis donnent davantage d'expérience.

Toutes ces règles forment un système.

---

# 4.2 Penser en systèmes

Le débutant conçoit souvent les mécaniques une par une.

Le game designer expérimenté pense en **réseau**.

Chaque nouvelle règle influence les autres.

Exemple :

Ajouter une nouvelle arme ne modifie pas uniquement le combat.

Elle influence aussi :

- l'économie ;
- la difficulté ;
- le crafting ;
- le loot ;
- les boss ;
- la progression.

Avant d'ajouter une fonctionnalité, posez-vous toujours cette question :

> **Quels autres systèmes vont être impactés ?**

---

# 4.3 Les composants d'un système

Un système est généralement composé de quatre éléments.

## Les entrées (Inputs)

Ce que le joueur ou le jeu fournit au système.

Exemples :

- argent ;
- temps ;
- énergie ;
- ressources ;
- compétences ;
- objets.

---

## Les traitements (Process)

Les règles qui transforment ces ressources.

Exemple :

10 minerais

↓

Forge

↓

1 épée

---

## Les sorties (Outputs)

Les résultats obtenus.

Exemples :

- équipement ;
- monnaie ;
- score ;
- progression ;
- accès à une nouvelle zone.

---

## Les contraintes

Ce qui limite le système.

Exemples :

- temps d'attente ;
- coût ;
- endurance ;
- inventaire limité ;
- niveau minimum.

Les contraintes empêchent le joueur d'obtenir tout immédiatement.

---

# 4.4 Les systèmes ouverts et fermés

## Les systèmes fermés

Ils ont peu de variables.

Le comportement est facilement prévisible.

Exemple :

Le Morpion.

Les règles sont fixes.

Les possibilités restent limitées.

Avantages :

- équilibrage simple ;
- comportement prévisible.

Inconvénients :

- faible émergence.

---

## Les systèmes ouverts

Ils offrent de nombreuses interactions.

Exemples :

- Minecraft
- RimWorld
- Dwarf Fortress
- The Sims

Le comportement du joueur devient difficile à prévoir.

Avantages :

- créativité ;
- émergence ;
- rejouabilité.

Inconvénients :

- équilibrage complexe ;
- nombreux cas particuliers.

---

# 4.5 Les propriétés émergentes

Une **propriété émergente** apparaît lorsqu'un comportement intéressant naît de la combinaison de règles simples.

Le concepteur ne programme pas directement ce comportement.

Il apparaît naturellement.

Exemple :

Dans Minecraft :

Le jeu ne demande jamais explicitement de construire un ordinateur.

Pourtant, les joueurs ont créé des calculateurs, des horloges et même des processeurs à l'aide de la Redstone.

Les règles simples produisent des créations complexes.

---

# 4.6 Les états

La plupart des objets possèdent un état.

Exemple :

Une porte peut être :

- fermée ;
- ouverte ;
- verrouillée ;
- cassée.

Chaque état modifie les interactions possibles.

Autre exemple :

Un personnage peut être :

- vivant ;
- blessé ;
- empoisonné ;
- étourdi ;
- mort.

Penser en états permet de créer des systèmes extensibles.

---

# 4.7 Les ressources

Les ressources sont des éléments consommables ou accumulables.

Exemples :

- or ;
- bois ;
- nourriture ;
- endurance ;
- mana ;
- réputation ;
- carburant.

Une bonne ressource répond à trois questions :

- Comment l'obtenir ?
- Comment la dépenser ?
- Pourquoi est-elle précieuse ?

Une ressource sans utilité devient inutile.

Une ressource trop abondante perd toute valeur.

---

# 4.8 Les sources et les puits (Sources & Sinks)

Pour qu'une économie reste stable, les ressources doivent entrer et sortir du système.

## Les sources

Ce qui produit des ressources.

Exemples :

- monstres ;
- quêtes ;
- récolte ;
- fabrication.

---

## Les puits

Ce qui détruit ou consomme les ressources.

Exemples :

- achat ;
- réparation ;
- crafting ;
- amélioration ;
- taxes ;
- entretien.

Sans puits, la richesse augmente sans limite.

Le joueur finit par ne plus avoir de décisions à prendre.

---

# 4.9 Les boucles de rétroaction (Feedback Loops)

Un système évolue grâce à des boucles de rétroaction.

Il en existe deux grandes catégories.

---

## Boucle positive (Positive Feedback Loop)

Une action renforce sa propre conséquence.

Exemple :

Le joueur gagne.

↓

Il obtient une meilleure arme.

↓

Il gagne plus facilement.

↓

Il obtient encore de meilleures armes.

Cette boucle accélère la progression.

Elle procure une sensation de puissance.

Mais utilisée sans contrôle, elle casse l'équilibrage.

---

## Boucle négative (Negative Feedback Loop)

Le système compense un avantage.

Exemple :

Dans un jeu de course :

Le premier reçoit peu d'aides.

Les derniers reçoivent des bonus.

Le but est de maintenir une compétition intéressante.

Les boucles négatives réduisent les écarts.

---

# 4.10 Les dépendances entre systèmes

Dans un jeu, aucun système n'existe isolément.

Exemple :

Combat

↓

Loot

↓

Économie

↓

Craft

↓

Progression

↓

Combat

Chaque système alimente les autres.

Si un seul est mal équilibré, l'ensemble du jeu est affecté.

---

# 4.11 Les systèmes de progression

Un système de progression peut agir sur plusieurs axes.

## Progression verticale

Le joueur devient plus puissant.

Exemples :

- dégâts ;
- santé ;
- armure.

---

## Progression horizontale

Le joueur obtient davantage d'options.

Exemples :

- nouvelles compétences ;
- nouveaux outils ;
- nouveaux styles de jeu.

La progression horizontale favorise la diversité plutôt que la puissance.

Les meilleurs RPG combinent souvent ces deux approches.

---

# 4.12 Les systèmes de risque et récompense

Chaque décision devrait comporter un compromis.

Exemple :

Explorer une grotte dangereuse.

Risques :

- mourir ;
- perdre du temps ;
- consommer des ressources.

Récompenses :

- équipement rare ;
- raccourci ;
- histoire ;
- ressources précieuses.

Si le risque est faible et la récompense énorme, le choix devient évident.

S'il est trop élevé pour une récompense dérisoire, le joueur l'ignore.

Le bon équilibre rend la décision intéressante.

---

# 4.13 Étude de cas : Slay the Spire

Le système est construit autour de plusieurs ressources :

- points de vie ;
- énergie ;
- cartes ;
- reliques ;
- or.

Chaque combat influence les suivants.

Dépenser trop de points de vie aujourd'hui peut empêcher de battre un boss plus tard.

Le jeu crée ainsi des décisions stratégiques permanentes.

Les systèmes sont simples individuellement, mais leurs interactions génèrent une grande profondeur.

---

# 4.14 Erreurs fréquentes

## Les systèmes isolés

Une mécanique qui n'interagit avec rien semble artificielle.

Chaque système important devrait avoir des liens avec plusieurs autres.

---

## Trop de ressources

Multiplier les monnaies complique inutilement le jeu.

Chaque ressource doit avoir un rôle clair.

---

## Inflation

Si le joueur accumule énormément d'or sans possibilité de le dépenser, la monnaie perd toute valeur.

Il faut créer des puits adaptés.

---

## Effet boule de neige incontrôlé

Une boucle positive mal maîtrisée rend rapidement le jeu trivial.

Prévoir des limites ou des mécanismes de compensation permet de préserver le défi.

---

## Complexité inutile

Ajouter des règles pour le simple plaisir d'ajouter des règles est rarement une bonne idée.

La profondeur naît souvent de l'interaction entre quelques systèmes simples.

---

# Exercices

## Exercice 1

Choisissez un jeu que vous connaissez.

Dessinez les liens entre :

- combat ;
- économie ;
- exploration ;
- progression ;
- crafting.

Quels systèmes dépendent les uns des autres ?

---

## Exercice 2

Concevez un système de crafting.

Définissez :

- les ressources nécessaires ;
- les recettes ;
- les contraintes ;
- les récompenses.

Comment ce système s'intègre-t-il à l'économie et à la progression ?

---

## Exercice 3

Identifiez une boucle de rétroaction dans un jeu.

Est-elle positive ou négative ?

Quels sont ses effets sur l'expérience du joueur ?

---

# À retenir

- Un système de jeu est un ensemble de règles interconnectées.
- Les systèmes efficaces reposent sur des interactions plutôt que sur une accumulation de mécaniques.
- Les propriétés émergentes donnent de la profondeur au gameplay.
- Les ressources doivent avoir des sources et des puits pour rester pertinentes.
- Les boucles de rétroaction positives accélèrent la progression, tandis que les boucles négatives régulent l'expérience.
- Chaque nouvelle règle doit être pensée en fonction de son impact sur les autres systèmes.

---

# Chapitre suivant

Dans le chapitre 5, nous étudierons le **Level Design** : comment construire des niveaux qui guident le joueur, enseignent les mécaniques, contrôlent le rythme et créent des expériences mémorables.
