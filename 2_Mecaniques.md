# 2. Les mécaniques de jeu et les Core Loops

## Objectifs pédagogiques

À la fin de ce chapitre, vous serez capable de :

- Comprendre ce qu'est une mécanique de jeu.
- Différencier une mécanique, un système et une boucle de gameplay.
- Concevoir un Core Loop solide.
- Identifier les mécaniques primaires et secondaires d'un jeu.
- Comprendre comment les mécaniques influencent les émotions du joueur.

---

# 2.1 Qu'est-ce qu'une mécanique de jeu ?

Une **mécanique de jeu** est une règle qui décrit ce que le joueur peut faire et comment le jeu réagit à cette action.

Autrement dit, une mécanique est une interaction entre le joueur et le système.

Exemples de mécaniques :

- Se déplacer
- Sauter
- Tirer
- Construire
- Miner
- Échanger
- Crafter
- Négocier
- Escalader
- Esquiver

Chaque mécanique possède :

- une entrée (input du joueur) ;
- une règle ;
- une conséquence.

Exemple :

**Input :**
Le joueur appuie sur le bouton "Saut".

↓

**Règle :**
Le personnage saute de 2 mètres.

↓

**Conséquence :**
Le joueur évite un obstacle.

---

# 2.2 Une mécanique n'est pas un système

Les débutants confondent souvent ces deux notions.

## Une mécanique

Une mécanique est une action.

Exemple :

- tirer ;
- courir ;
- parler à un PNJ.

---

## Un système

Un système est un ensemble de mécaniques qui interagissent.

Exemple :

Le système de combat d'un RPG comprend :

- les attaques ;
- les esquives ;
- les critiques ;
- les armes ;
- les résistances ;
- les effets élémentaires ;
- les compétences.

Aucune de ces mécaniques n'est intéressante seule.

C'est leur combinaison qui crée la profondeur.

---

# 2.3 Les catégories de mécaniques

Toutes les mécaniques peuvent être regroupées en grandes familles.

## Déplacement

Le joueur change de position.

Exemples :

- marcher ;
- courir ;
- glisser ;
- voler ;
- nager ;
- grimper.

Émotions produites :

- liberté ;
- exploration ;
- vitesse.

---

## Combat

Le joueur affronte une menace.

Exemples :

- attaques ;
- blocage ;
- parade ;
- esquive ;
- magie ;
- armes.

Émotions :

- tension ;
- adrénaline ;
- maîtrise.

---

## Exploration

Le joueur découvre.

Exemples :

- carte ouverte ;
- brouillard de guerre ;
- secrets ;
- collectibles.

Émotions :

- curiosité ;
- émerveillement.

---

## Gestion

Le joueur prend des décisions stratégiques.

Exemples :

- économie ;
- nourriture ;
- ressources ;
- énergie.

Émotions :

- planification ;
- optimisation.

---

## Création

Le joueur fabrique.

Exemples :

- crafting ;
- construction ;
- personnalisation.

Émotions :

- créativité ;
- expression personnelle.

---

## Social

Le joueur interagit avec d'autres joueurs.

Exemples :

- commerce ;
- guildes ;
- coopération ;
- diplomatie.

Émotions :

- appartenance ;
- compétition.

---

# 2.4 Les mécaniques primaires et secondaires

Tous les jeux possèdent une hiérarchie.

## Mécaniques primaires

Ce sont celles utilisées en permanence.

Exemple : Mario

- courir ;
- sauter.

90 % du jeu repose dessus.

---

## Mécaniques secondaires

Elles enrichissent le gameplay.

Exemples :

- récupérer une étoile ;
- utiliser un costume ;
- piloter un véhicule.

Elles apportent de la variété.

---

# 2.5 Les Core Loops

Le Core Loop est la boucle principale répétée pendant tout le jeu.

Le joueur exécute cette boucle plusieurs centaines, voire plusieurs milliers de fois.

Un mauvais Core Loop rend le jeu répétitif.

Un bon Core Loop reste satisfaisant longtemps.

---

## Exemple : Minecraft

Récolter

↓

Fabriquer

↓

Construire

↓

Explorer

↓

Récolter

La boucle recommence.

---

## Exemple : Diablo

Explorer

↓

Combattre

↓

Obtenir du loot

↓

Devenir plus fort

↓

Explorer une zone plus difficile

---

## Exemple : FIFA

Récupérer le ballon

↓

Construire une attaque

↓

Tirer

↓

Marquer

↓

Recommencer

---

# 2.6 Les boucles secondaires

Autour du Core Loop gravitent d'autres boucles.

Exemple :

Core Loop :

Combattre

↓

Loot

↓

Progression

Boucles secondaires :

- artisanat ;
- commerce ;
- réputation ;
- quêtes ;
- collection.

Ces boucles augmentent la durée de vie du jeu.

---

# 2.7 Les boucles de progression

Une progression efficace repose sur une alternance entre effort et récompense.

Exemple :

Mission

↓

XP

↓

Niveau supérieur

↓

Nouvelle compétence

↓

Mission plus difficile

Cette progression donne au joueur le sentiment de devenir plus puissant.

---

# 2.8 Les boucles émotionnelles

Toutes les boucles ne servent pas uniquement à faire progresser le joueur.

Elles peuvent créer une émotion.

Exemple dans un jeu d'horreur :

Explorer

↓

Entendre un bruit

↓

Chercher la source

↓

Trouver un monstre

↓

Fuir

↓

Respirer

↓

Explorer

Le joueur alterne entre stress et soulagement.

---

# 2.9 Les boucles économiques

Très présentes dans les jeux de gestion.

Exemple :

Récolter du bois

↓

Construire une scierie

↓

Produire plus de bois

↓

Construire davantage

↓

Développer la ville

Le plaisir vient de l'optimisation.

---

# 2.10 Les verbes du joueur

Le game designer réfléchit souvent en termes de verbes.

Quels sont les verbes principaux ?

Exemple :

The Legend of Zelda

- explorer ;
- combattre ;
- résoudre ;
- pousser ;
- escalader ;
- cuisiner.

Chaque verbe ouvre de nouvelles possibilités.

---

# 2.11 Ajouter une mécanique : attention au coût

Chaque nouvelle mécanique possède un coût.

Elle nécessite :

- du développement ;
- des animations ;
- des effets sonores ;
- des tests ;
- de l'équilibrage ;
- des tutoriels ;
- de l'interface.

Une mécanique peu utilisée est souvent une mauvaise idée.

Le meilleur design est souvent le plus simple.

---

# 2.12 La profondeur émerge de la combinaison

Un jeu profond n'a pas forcément beaucoup de mécaniques.

Exemple :

Les échecs possèdent très peu de règles.

Pourtant :

- les stratégies sont infinies ;
- les situations sont variées ;
- les parties sont toutes différentes.

La profondeur provient de la combinaison des règles.

C'est ce qu'on appelle le **gameplay émergent**.

---

# 2.13 Étude de cas : Portal

Portal repose sur seulement quelques mécaniques :

- marcher ;
- sauter ;
- créer deux portails ;
- transporter des cubes.

Pourtant, ces mécaniques permettent de créer des centaines d'énigmes différentes.

Pourquoi ?

Parce que les règles sont simples mais se combinent de nombreuses façons.

C'est un excellent exemple de profondeur obtenue avec peu de mécaniques.

---

# 2.14 Erreurs fréquentes des débutants

## Ajouter trop de mécaniques

Le joueur est perdu.

---

## Changer constamment les règles

Le joueur ne maîtrise jamais le jeu.

---

## Introduire une mécanique puis ne plus l'utiliser

Le joueur oublie son existence.

---

## Empiler des fonctionnalités sans cohérence

Le gameplay devient confus.

---

## Copier les mécaniques d'un autre jeu sans comprendre leur rôle

Une mécanique n'est pertinente que si elle sert l'expérience recherchée.

---

# Exercices

## Exercice 1

Choisissez un jeu.

Listez :

- les mécaniques principales ;
- les mécaniques secondaires.

---

## Exercice 2

Dessinez le Core Loop d'un jeu que vous aimez.

Utilisez des flèches.

---

## Exercice 3

Inventez un jeu en utilisant seulement trois verbes.

Exemple :

- Explorer
- Photographier
- S'échapper

Décrivez ensuite le Core Loop correspondant.

---

## Exercice 4

Imaginez une nouvelle mécanique pour un jeu existant.

Répondez aux questions suivantes :

- Quel problème résout-elle ?
- Quelle émotion apporte-t-elle ?
- Comment s'intègre-t-elle au Core Loop ?
- Quels sont ses coûts de développement ?

---

# À retenir

- Une mécanique est une action que le joueur peut réaliser.
- Un système est un ensemble de mécaniques qui interagissent.
- Le **Core Loop** est la boucle principale répétée pendant toute la partie.
- Les meilleures mécaniques sont simples à comprendre mais riches en possibilités.
- La profondeur d'un jeu provient souvent de la combinaison des règles, et non de leur quantité.
- Chaque nouvelle mécanique doit renforcer l'expérience de jeu et s'intégrer naturellement aux boucles existantes.

---

# Chapitre suivant

Dans le chapitre 3, nous étudierons la psychologie du joueur : motivation, théorie du Flow, récompenses, autonomie, maîtrise et les mécanismes qui donnent envie de continuer à jouer.
