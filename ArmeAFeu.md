# Ajouter une arme à feu et tirer dans Unreal Engine 5.6 (Blueprint)

> **Niveau :** Débutant / Intermédiaire
> **Moteur :** Unreal Engine 5.6
> **Langage :** Blueprint uniquement

## Objectifs

- Créer une arme en Blueprint.
- Attacher l'arme au personnage.
- Tirer avec le clic gauche.
- Faire apparaître un projectile.
- Détecter les collisions.
- Infliger des dégâts.
- Ajouter des effets visuels et sonores.
- Gérer les munitions.

---

# Architecture

```text
Content
├── Blueprints
│   ├── BP_Player
│   ├── BP_Weapon
│   ├── BP_Bullet
│   └── BP_Target
├── FX
├── Sounds
└── Meshes
```

## 1. Créer le projectile

Créer **BP_Bullet** (Parent : `Actor`).

### Composants

- Sphere Collision (Root)
- Static Mesh
- Projectile Movement

### Projectile Movement

- Initial Speed : `5000`
- Max Speed : `5000`
- Rotation Follows Velocity : `True`
- Should Bounce : `False`
- Gravity Scale : `0`

## 2. Détruire le projectile

```text
Event Hit
    ↓
Destroy Actor
```

## 3. Ajouter les dégâts

Créer une variable :

- `Damage` (Float) = `25`

Blueprint :

```text
Event Hit
    ↓
Apply Damage
    Damaged Actor = Other Actor
    Base Damage = Damage
    Damage Causer = Self
    Event Instigator = Get Instigator
    ↓
Destroy Actor
```

## 4. Créer l'arme

Créer **BP_Weapon** (Parent : `Actor`).

Composants :

- Scene (Root)
- Skeletal Mesh
- Muzzle (Scene)

Le composant **Muzzle** représente la sortie du canon.

## 5. Variables

- `ProjectileClass` : BP_Bullet Class Reference
- `FireRate` : Float = `0.15`
- `Ammo` : Integer = `30`
- `MaxAmmo` : Integer = `30`

## 6. Fonction Fire

```text
Branch (Ammo > 0 ?)
    ↓
Ammo--
    ↓
Spawn Actor From Class
Class = ProjectileClass
Spawn Transform = Muzzle → Get World Transform
```

## 7. Attacher l'arme

Dans `BP_Player` :

```text
BeginPlay
    ↓
Spawn Actor From Class (BP_Weapon)
    ↓
Attach Actor To Component
Parent = Mesh
Socket = weapon_socket
```

Créer le socket `weapon_socket` sur `hand_r`.

## 8. Tir

Créer une Input Action `IA_Fire`.

```text
Input Action Fire
    ↓
Weapon → Fire
```

## 9. Cadence de tir

Variable :

- `CanFire` : Bool = `True`

```text
CanFire ?
    ↓
Set CanFire = False
    ↓
Spawn Projectile
    ↓
Delay(FireRate)
    ↓
Set CanFire = True
```

## 10. Son

Utiliser :

```text
Spawn Sound Attached
```

## 11. Flash de bouche

Utiliser :

```text
Spawn System Attached
```

sur le composant `Muzzle`.

## 12. Cible

Créer `BP_Target`.

Variable :

- `Health` = `100`

```text
Event Any Damage
    ↓
Health -= Damage
    ↓
Health <= 0 ?
    ↓
Destroy Actor
```

## 13. Rechargement

Créer une Input Action `Reload`.

```text
Ammo = MaxAmmo
```

## 14. Empêcher le tir sans munitions

```text
Ammo > 0 ?
    ├── Oui → Fire
    └── Non → Play Empty Sound
```

## 15. Débogage

Utiliser :

```text
Draw Debug Line
```

pour visualiser la direction du tir.

---

# Résumé

```text
Clic gauche
    ↓
Character
    ↓
Weapon.Fire()
    ↓
Ammo--
    ↓
Spawn Projectile
    ↓
Collision
    ↓
Apply Damage
    ↓
Destroy Projectile
```
