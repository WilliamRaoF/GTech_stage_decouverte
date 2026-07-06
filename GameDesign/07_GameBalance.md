# 7. L'équilibrage (Game Balance)

## Objectifs pédagogiques

À la fin de ce chapitre, vous serez capable de :

- Comprendre ce qu'est le Game Balance.
- Identifier les différents types d'équilibrage.
- Ajuster la difficulté d'un jeu.
- Équilibrer des armes, des personnages et des ressources.
- Utiliser les données de playtests pour améliorer un jeu.
- Éviter les erreurs classiques d'équilibrage.

---

# 7.1 Qu'est-ce que le Game Balance ?

Le **Game Balance** est le processus qui consiste à ajuster les règles d'un jeu afin que l'expérience soit :

- amusante ;
- juste ;
- variée ;
- stimulante.

L'équilibrage ne signifie pas que tout doit être parfaitement égal.

Il signifie que **chaque option proposée au joueur possède une valeur et un intérêt**.

Un jeu est équilibré lorsque les choix du joueur sont intéressants, et non lorsqu'ils sont identiques.

---

# 7.2 Pourquoi équilibrer ?

Sans équilibrage, plusieurs problèmes apparaissent rapidement.

Exemples :

- une arme est tellement puissante que toutes les autres deviennent inutiles ;
- une stratégie est toujours meilleure que les autres ;
- une compétence est indispensable ;
- une ressource n'a plus aucune valeur.

Lorsque cela arrive, le joueur ne choisit plus.

Il applique simplement la solution optimale.

Or, le plaisir vient souvent de la prise de décision.

---

# 7.3 Les différents types d'équilibrage

## Équilibrage de la difficulté

Le défi doit évoluer progressivement.

Le joueur doit :

- apprendre ;
- maîtriser ;
- être mis au défi.

---

## Équilibrage des ressources

Toutes les ressources doivent avoir :

- une utilité ;
- une rareté ;
- une méthode d'acquisition.

Une ressource infinie perd toute valeur.

---

## Équilibrage des personnages

Dans un jeu comportant plusieurs personnages, chacun doit posséder :

- des forces ;
- des faiblesses ;
- un style de jeu identifiable.

---

## Équilibrage des armes

Une arme n'est pas équilibrée parce qu'elle inflige les mêmes dégâts qu'une autre.

Elle est équilibrée lorsqu'elle possède des avantages compensés par des inconvénients.

Exemple :

Épée :

- rapide ;
- faible portée.

Lance :

- lente ;
- grande portée.

Arc :

- très longue portée ;
- faible efficacité au corps à corps.

---

# 7.4 Le triangle des choix

Une bonne option implique toujours un compromis.

Par exemple :

Arme A

- très puissante ;
- lente ;
- lourde.

Arme B

- peu puissante ;
- très rapide ;
- légère.

Les deux armes deviennent intéressantes selon le contexte.

À éviter :

Une arme qui est :

- plus puissante ;
- plus rapide ;
- plus légère.

Elle rend immédiatement toutes les autres obsolètes.

---

# 7.5 La courbe de difficulté

La difficulté doit évoluer avec les compétences du joueur.

Une progression classique ressemble à ceci :

Introduction

↓

Découverte

↓

Maîtrise

↓

Nouveau défi

↓

Nouvelle mécanique

↓

Boss

↓

Respiration

↓

Nouvelle zone

Chaque nouvelle mécanique augmente progressivement la complexité.

---

# 7.6 Les statistiques

Les statistiques servent à représenter quantitativement les capacités d'un personnage ou d'un objet.

Exemples :

- santé ;
- dégâts ;
- vitesse ;
- portée ;
- précision ;
- endurance ;
- mana.

Attention :

Chaque statistique supplémentaire augmente la complexité du jeu.

Avant d'ajouter une nouvelle statistique, demandez-vous :

> Apporte-t-elle une nouvelle décision intéressante ?

---

# 7.7 Les formules

Le game designer travaille souvent avec des formules simples.

Exemple :

```
Dégâts = Attaque - Défense
```

Ou :

```
Dégâts = Attaque × Multiplicateur
```

Les formules doivent être :

- prévisibles ;
- cohérentes ;
- faciles à ajuster.

Les développeurs utilisent souvent des feuilles de calcul pour tester différentes valeurs avant leur implémentation.

---

# 7.8 Les rendements décroissants

Les **rendements décroissants** empêchent certaines statistiques de devenir excessivement puissantes.

Exemple :

Les premiers points d'armure réduisent fortement les dégâts.

Puis chaque point supplémentaire apporte un bénéfice de plus en plus faible.

Cela encourage le joueur à diversifier son équipement plutôt qu'à investir dans une seule statistique.

---

# 7.9 Les ressources rares

La rareté donne de la valeur.

Exemples :

- potion de soin ;
- flèches ;
- monnaie ;
- matériaux rares.

Une ressource trop abondante devient insignifiante.

Une ressource trop rare peut bloquer la progression.

Le bon équilibre dépend de l'expérience recherchée.

---

# 7.10 Les récompenses

Une récompense doit être proportionnelle à l'effort demandé.

Un défi difficile mérite une récompense importante.

À l'inverse, une tâche triviale ne devrait pas offrir un objet exceptionnel.

Une mauvaise répartition des récompenses peut casser toute la progression.

---

# 7.11 Les difficultés artificielles

Toutes les difficultés ne sont pas intéressantes.

## Bonne difficulté

Le joueur échoue parce qu'il doit apprendre.

Exemples :

- meilleur timing ;
- meilleure stratégie ;
- observation.

---

## Mauvaise difficulté

Le joueur échoue à cause :

- d'une caméra imprécise ;
- d'une interface confuse ;
- d'un manque d'informations ;
- de contrôles peu fiables.

Ces difficultés doivent être éliminées.

---

# 7.12 Les métriques

L'équilibrage ne repose pas uniquement sur l'intuition.

Les studios analysent des données.

Exemples :

- temps moyen d'un niveau ;
- nombre de morts ;
- arme la plus utilisée ;
- compétence la plus choisie ;
- taux d'abandon ;
- ressources accumulées.

Ces informations permettent d'identifier les déséquilibres.

---

# 7.13 Les playtests

Le meilleur outil d'équilibrage reste le playtest.

Pendant un test :

- observer ;
- prendre des notes ;
- éviter d'aider le joueur.

Les questions importantes :

- Où meurt-il ?
- Où s'ennuie-t-il ?
- Quelles armes ignore-t-il ?
- Quels objets n'utilise-t-il jamais ?
- Où est-il perdu ?

Les réponses guident les ajustements.

---

# 7.14 Les méthodes d'équilibrage

## Buff

Améliorer une option.

Exemple :

Augmenter les dégâts d'une arme peu utilisée.

---

## Nerf

Réduire la puissance d'une option.

Exemple :

Réduire la portée d'un personnage dominant.

---

## Rework

Modifier complètement le fonctionnement d'une mécanique.

Parfois, augmenter ou diminuer une valeur ne suffit pas.

Il faut revoir la conception.

---

# 7.15 Le Meta

Le **Meta** correspond aux stratégies les plus efficaces découvertes par la communauté.

Dans un jeu multijoueur, le Meta évolue constamment.

Les développeurs doivent surveiller :

- les statistiques ;
- les compétitions ;
- les retours des joueurs.

L'objectif n'est pas de supprimer le Meta.

Il est de faire en sorte que plusieurs stratégies restent viables.

---

# 7.16 Étude de cas : Mario Kart

Les objets distribués aux joueurs dépendent souvent de leur position.

Le premier reçoit des bonus modestes.

Les derniers obtiennent parfois :

- une étoile ;
- un Bullet Bill ;
- un éclair.

Il s'agit d'une **boucle de rétroaction négative** destinée à maintenir le suspense.

L'objectif est que la course reste intéressante jusqu'à la fin.

---

# 7.17 Étude de cas : Dark Souls

Les ennemis infligent des dégâts élevés.

Cependant :

- les contrôles sont précis ;
- les animations sont lisibles ;
- les règles restent constantes.

Le joueur accepte donc la difficulté.

La frustration provient de ses erreurs, et non d'un système injuste.

---

# 7.18 Erreurs fréquentes

## Tout équilibrer

Toutes les situations n'ont pas besoin d'être parfaitement symétriques.

Une légère asymétrie peut rendre le jeu plus riche.

---

## Modifier trop souvent

Changer constamment les statistiques désoriente les joueurs.

Les ajustements doivent être mesurés.

---

## Se fier uniquement aux chiffres

Une arme peut sembler équilibrée sur le papier mais être désagréable à utiliser.

Les sensations restent essentielles.

---

## Ignorer les joueurs

Les retours des joueurs ne sont pas toujours des solutions.

En revanche, ils révèlent souvent des problèmes réels.

Le game designer doit écouter les problèmes sans appliquer automatiquement les solutions proposées.

---

# Exercices

## Exercice 1

Concevez trois armes.

Pour chacune, définissez :

- dégâts ;
- portée ;
- cadence ;
- vitesse ;
- coût.

Aucune ne doit être objectivement meilleure que les autres.

---

## Exercice 2

Imaginez une économie simple.

Définissez :

- les sources d'or ;
- les puits d'or ;
- les objets achetables ;
- la progression des prix.

Testez si le joueur peut accumuler trop d'argent.

---

## Exercice 3

Analysez un jeu que vous connaissez.

Répondez aux questions suivantes :

- Quelle stratégie est dominante ?
- Pourquoi ?
- Comment pourriez-vous la rééquilibrer sans la rendre inutile ?

---

# À retenir

- Le Game Balance consiste à rendre les choix intéressants plutôt qu'identiques.
- Les armes, compétences et personnages doivent être différenciés par des compromis.
- Une bonne courbe de difficulté accompagne la progression du joueur.
- Les statistiques et les formules doivent rester simples et lisibles.
- Les données de playtests sont indispensables pour valider un équilibrage.
- Les ajustements passent par des buffs, des nerfs ou des reworks selon les besoins.
- Un bon équilibrage favorise la diversité des stratégies plutôt que l'existence d'une solution unique.

---

# Chapitre suivant

Dans le chapitre 8, nous étudierons **la narration interactive (Narrative Design)** : construction d'univers, personnages, quêtes, dialogues, narration environnementale, choix du joueur et intégration de l'histoire au gameplay.
