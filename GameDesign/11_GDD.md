# 11. Le Game Design Document (GDD)

## Objectifs pédagogiques

À la fin de ce chapitre, vous serez capable de :

- Comprendre le rôle d'un Game Design Document (GDD).
- Structurer un document de conception professionnel.
- Communiquer efficacement avec les différentes équipes.
- Décrire des mécaniques de manière claire et exploitable.
- Documenter un projet tout au long de son développement.
- Utiliser un GDD comme outil de communication plutôt que comme simple documentation.

---

# 11.1 Qu'est-ce qu'un Game Design Document ?

Le **Game Design Document**, ou **GDD**, est le document qui décrit le fonctionnement du jeu.

Il centralise toutes les informations nécessaires à sa conception.

Le GDD répond à une question essentielle :

> **Comment fonctionne le jeu ?**

Contrairement à une idée reçue, un GDD n'est pas un roman.

C'est un document technique destiné à être consulté quotidiennement par les membres de l'équipe.

---

# 11.2 À quoi sert un GDD ?

Le GDD permet :

- d'expliquer la vision du projet ;
- d'aligner les équipes ;
- d'éviter les ambiguïtés ;
- de documenter les décisions ;
- de faciliter l'intégration de nouveaux membres ;
- de suivre l'évolution du projet.

Sans documentation, chaque membre peut interpréter différemment une même mécanique.

Le GDD réduit ces risques.

---

# 11.3 Le GDD n'est pas figé

Le GDD est un document vivant.

Il évolue avec le projet.

Chaque playtest peut conduire à modifier :

- une mécanique ;
- une statistique ;
- un niveau ;
- une interface.

Le document doit être mis à jour régulièrement.

Un GDD obsolète devient rapidement inutile.

---

# 11.4 Les qualités d'un bon GDD

Un bon document est :

- clair ;
- concis ;
- structuré ;
- illustré ;
- facile à rechercher.

Évitez les longs paragraphes.

Préférez :

- listes ;
- tableaux ;
- schémas ;
- captures d'écran ;
- diagrammes.

---

# 11.5 Structure générale

Bien que chaque studio adapte son format, un GDD contient généralement les sections suivantes.

---

# Vision du projet

Elle présente :

- le concept ;
- les objectifs ;
- les intentions de design.

Exemple :

> "Créer un jeu d'aventure coopératif mettant l'accent sur l'exploration et la résolution d'énigmes."

Cette section sert de référence tout au long du développement.

---

# Présentation générale

Informations essentielles :

- titre ;
- genre ;
- plateforme ;
- moteur ;
- public cible ;
- nombre de joueurs.

---

# Le Pitch

Le pitch résume le projet en quelques phrases.

Exemple :

> "Un jeu de survie coopératif où quatre explorateurs reconstruisent une civilisation sur une planète hostile."

Le pitch doit être compréhensible en moins d'une minute.

---

# Les piliers du Game Design

Les piliers définissent les valeurs fondamentales du projet.

Exemple :

- coopération ;
- exploration ;
- liberté ;
- émergence.

Chaque nouvelle fonctionnalité doit renforcer ces piliers.

---

# Références

Présentez :

- jeux similaires ;
- inspirations artistiques ;
- inspirations techniques.

Attention :

Une référence n'est pas une copie.

Elle sert uniquement à illustrer une intention.

---

# 11.6 Gameplay

Cette partie décrit précisément les actions du joueur.

Exemple :

Déplacement

- marcher ;
- courir ;
- grimper ;
- nager.

Combat

- attaque légère ;
- attaque lourde ;
- esquive ;
- parade.

Interaction

- ouvrir ;
- pousser ;
- ramasser ;
- discuter.

Chaque mécanique doit être documentée.

---

## Exemple de fiche mécanique

### Nom

Esquive

### Description

Permet d'éviter une attaque pendant une courte durée.

### Contrôle

Touche Espace.

### Conditions

- endurance suffisante ;
- personnage au sol.

### Résultat

- déplacement rapide ;
- invulnérabilité pendant 0,3 seconde.

### Feedback

- animation ;
- son ;
- particules.

---

# 11.7 Les systèmes

Chaque système possède sa propre documentation.

Exemple :

Système d'expérience

- calcul des gains ;
- montée de niveau ;
- statistiques.

---

Système économique

- monnaie ;
- boutiques ;
- crafting ;
- ventes.

---

Système météo

- pluie ;
- neige ;
- brouillard ;
- conséquences sur le gameplay.

---

# 11.8 Les niveaux

Chaque niveau possède généralement :

- un objectif ;
- un plan ;
- les ennemis ;
- les objets ;
- les événements ;
- les récompenses.

Les Level Designers utilisent souvent des cartes annotées.

---

# 11.9 Les personnages

Chaque personnage possède une fiche.

Informations courantes :

- rôle ;
- histoire ;
- personnalité ;
- statistiques ;
- compétences ;
- animations.

Pour les ennemis :

- comportement ;
- IA ;
- points faibles ;
- récompenses.

---

# 11.10 Les interfaces

Le GDD décrit également :

- HUD ;
- menus ;
- inventaire ;
- cartes ;
- fenêtres.

Les wireframes sont très utiles.

Ils montrent l'organisation des éléments sans produire les graphismes définitifs.

---

# 11.11 Les boucles de gameplay

Le document présente souvent :

Core Loop

↓

Boucles secondaires

↓

Progression

↓

End Game

Ces schémas permettent aux équipes de comprendre rapidement la structure globale.

---

# 11.12 Les variables

Chaque valeur importante doit être documentée.

Exemple :

Santé maximale :

100

Potion :

+30 PV

Attaque :

18 dégâts

Temps de recharge :

8 secondes

Les développeurs peuvent ensuite modifier facilement ces paramètres.

---

# 11.13 Les diagrammes

Les schémas simplifient énormément la communication.

Exemples :

Diagrammes de flux

```
Explorer

↓

Combattre

↓

Loot

↓

Craft

↓

Explorer
```

Diagrammes d'états

```
Idle

↓

Marche

↓

Course

↓

Saut

↓

Atterrissage

↓

Idle
```

Ces représentations sont souvent plus efficaces que plusieurs pages de texte.

---

# 11.14 Les outils professionnels

Les studios utilisent rarement un document Word unique.

Les outils les plus courants sont :

## Notion

Documentation collaborative.

Très utilisé par les studios indépendants.

---

## Confluence

Documentation professionnelle.

Très répandu dans les grandes entreprises.

---

## Google Docs

Simple et collaboratif.

---

## Miro

Parfait pour :

- schémas ;
- cartes mentales ;
- wireframes.

---

## Figma

Documentation des interfaces.

---

## Jira

Suivi des tâches.

Le GDD est souvent relié directement aux tickets de développement.

---

# 11.15 Les erreurs fréquentes

## Trop de texte

Un GDD n'est pas un roman.

Les développeurs doivent trouver rapidement une information.

---

## Informations contradictoires

Toutes les sections doivent être cohérentes.

Une valeur différente dans deux pages crée immédiatement de la confusion.

---

## Absence de mise à jour

Le document doit évoluer avec le projet.

Une documentation obsolète devient dangereuse.

---

## Trop de détails trop tôt

Les premières versions du GDD restent volontairement légères.

Les détails apparaissent progressivement.

---

## Absence de vision

Documenter des mécaniques sans expliquer l'expérience recherchée conduit souvent à un projet incohérent.

---

# 11.16 Exemple simplifié de GDD

## Nom

Sky Ruins

---

## Genre

Action-Aventure

---

## Plateformes

PC

Nintendo Switch

---

## Public

12+

---

## Pitch

Explorer des îles flottantes afin de restaurer une civilisation disparue.

---

## Core Loop

Explorer

↓

Résoudre des énigmes

↓

Obtenir une relique

↓

Débloquer une nouvelle capacité

↓

Explorer une nouvelle île

---

## Piliers

- Exploration
- Découverte
- Verticalité
- Narration environnementale

---

## Mécaniques

- escalade
- vol plané
- combat léger
- énigmes

---

## Progression

5 grandes régions

15 compétences

40 reliques

---

# 11.17 Étude de cas : Ubisoft

Dans les grands studios, un GDD complet peut être réparti en plusieurs centaines de pages.

Chaque système possède son propre document :

- combat ;
- IA ;
- économie ;
- progression ;
- interface ;
- narration.

L'objectif est que chaque équipe dispose uniquement des informations qui la concernent.

---

# 11.18 Étude de cas : Studios indépendants

Les petits studios utilisent souvent un GDD beaucoup plus léger.

Une documentation de 20 à 50 pages suffit parfois.

Le document évolue rapidement au fil des prototypes.

La simplicité est souvent préférable à une documentation gigantesque jamais mise à jour.

---

# Exercices

## Exercice 1

Rédigez le pitch de votre jeu.

Maximum :

150 mots.

---

## Exercice 2

Définissez les trois piliers de votre projet.

Pour chacun, expliquez :

- pourquoi il est important ;
- comment il influence le gameplay.

---

## Exercice 3

Créez une fiche de mécanique.

Incluez :

- objectif ;
- contrôles ;
- règles ;
- feedbacks ;
- variables.

---

## Exercice 4

Dessinez la Core Loop de votre jeu.

Ajoutez ensuite :

- les boucles secondaires ;
- les systèmes ;
- les récompenses.

---

# À retenir

- Le GDD est avant tout un outil de communication.
- Il doit être clair, vivant et régulièrement mis à jour.
- Une bonne documentation facilite la collaboration entre les équipes.
- Les mécaniques, systèmes, interfaces et niveaux doivent être documentés de manière précise.
- Les schémas et les tableaux sont souvent plus efficaces que de longs textes.
- La documentation accompagne le projet du prototype jusqu'à la production.

---

# Chapitre suivant

Dans le dernier chapitre, nous verrons **la production d'un jeu vidéo** : organisation d'une équipe, méthodes Agile, Scrum, gestion des tâches, jalons de production (Milestones), gestion des risques, rôle du Producteur et cycle complet de développement, de l'idée jusqu'à la sortie du jeu.
