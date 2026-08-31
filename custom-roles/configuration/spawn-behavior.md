---
icon: person-falling
---

# Spawn Behavior

Spawning is definitely the most important mechanics for a Custom Role.\
With UCR you can decide almost everything, from the location, to the conditions: almost everything!

The object should look like this:

```yaml
spawn_settings:
  can_replace_roles:
  - ClassD
  max_players: 10
  min_players: 1
  spawn_chance: 60
  spawn_delay: 0
  spawn: RoomsSpawn
  spawn_zones: []
  spawn_rooms:
  - LczClassDSpawn
  spawn_roles:
  - ClassD
  spawn_points: []
  required_permission: ''
```

### Can Replace Roles

**Configuration element name:** `can_replace_roles` \
**Type:** [`[]RoleTypeId`](../../syntax-notions/enums.md#roletypeid-and-team)

**This configuration value contains Enum values**: please visit the [Enums](../../syntax-notions/enums.md) page in order to learn more about them!

A list of vanilla roles that can be replaced by this Custom Role.\
For example, if you put only `ClassD` then the role will be able to spawn only at the beginning of the round and it would be given only to a Class-D!

This is the easiest way to control which vanilla-roles can become Custom Roles and it's also a powerful tool to choose _when_ a Custom Role can spawn.

When `spawn_delay` is used, this list means something slightly different: it selects the players the Custom Role is handed to once the delay has elapsed. See [Spawn Delay](spawn-behavior.md#spawn-delay).

### Max Players

**Configuration element name:** `max_players` \
**Type:** `int32`&#x20;

The maximum number of players that can have this Custom Role simultaneously.

### Min Players

**Configuration element name:** `min_players` \
**Type:** `int32`&#x20;

The minimum number of players that **must be** online in the server in order to allow the spawn of this Custom Role.

### Spawn Chance

**Configuration element name:** `spawn_chance` \
**Type:** `int32`&#x20;

The chance of spawning as this Custom Role (if your vanilla role was in the `can_replace_roles` list) in percentage (%).\
`spawn_chance: 60` is a 60% chance of spawning.

### Spawn Delay

**Configuration element name:** `spawn_delay`\
**Type:** `float`

How many seconds after the round starts the Custom Role is spawned. The default, `0`, keeps the role on the normal spawn evaluation: it replaces one of its `can_replace_roles` the moment that vanilla role spawns.

Any value above `0` takes the role out of the spawning. Instead, UCR waits the configured number of seconds after the round starts and then converts the players who hold one of the roles listed in `can_replace_roles`, up to `max_players`, rolling `spawn_chance` for each role.

Listing `Spectator` in `can_replace_roles` is what makes the role select players from `Spectator` mid-round, rather than taking someone who is already playing:

```yaml
spawn_settings:
  can_replace_roles:
  - Spectator
  max_players: 4
  min_players: 1
  spawn_chance: 100
  spawn_delay: 180
  spawn: RoomsSpawn
  spawn_zones: []
  spawn_rooms:
  - LczClassDSpawn
  spawn_roles:
  - ClassD
  spawn_points: []
  required_permission: ''
```

Three minutes into the round, one random spectator (as long as at least 4 players are on the server) is spawned as this Custom Role in the Class-D spawn room.

Converting players who are already alive works the same way — list their roles instead:

```yaml
spawn_settings:
  can_replace_roles:
  - Spectator
  max_players: 3
  min_players: 1
  spawn_chance: 100
  spawn_delay: 180
  spawn: KeepCurrentPositionSpawn
  spawn_zones: []
  spawn_rooms:
  - LczClassDSpawn
  spawn_roles:
  - ClassD
  spawn_points: []
  required_permission: ''
```

Two minutes in, every Class-D still alive has a 25% chance of turning into this Custom Role where they stand, until 3 of them have.

Notes:

* The delay is counted from the moment the round's roles are assigned, and it only fires once per round.
* `can_replace_roles` is not limited to the roles the instant spawn evaluation supports — any role a player can actually hold works, `Spectator` included.
* Players who already have a Custom Role are never picked.
* Nothing is spawned if the round ends before the delay elapses.
* Roles reloaded with `ucr reload` mid-round are scheduled from the next round onwards.
* `ucr percentages` lists timer-based roles in their own section, since they are not part of the spawn draw.

### Spawn

**Configuration element name:** `spawn` \
**Type:** [`SpawnType`](../../syntax-notions/enums.md#spawntype)&#x20;

**This configuration value contains an Enum**: please visit the [Enums](../../syntax-notions/enums.md) page in order to learn more about them!

The spawn mechanism that UCR will use in order to decide where to spawn your Custom Role.\
Available values:\
\- `CompleteRandomSpawn`: a random room inside the whole facility will be chosen.\
\- `ZoneSpawn`: the role will spawn in a room in one of the given Zones\
\- `RoomsSpawn`: the role will spawn in one of the given Rooms.\
\- `SpawnPointSpawn`: the role will spawn in one of the given Spawn Points.\
\- `KeepRoleSpawn`: the role will keep the default [vanilla Role](configuration-elements.md#role) position, chosen by the game.\
\- `KeepCurrentPositionSpawn`: the role won't modify the player position (where they spawned as the [vanilla Role](configuration-elements.md#role))\
\- `ClassDCell`: the role will spawn in one of the Class-D's cells.\
\- `RoleSpawn`: the role will be spawned in a random spawn position of one of the given Spawn Roles.

### Spawn Zones

**Configuration element name:** `spawn_zones` \
**Type:** [`[]ZoneType`](../../syntax-notions/enums.md#zonetype)&#x20;

**This configuration value contains Enum values**: please visit the [Enums](../../syntax-notions/enums.md) page in order to learn more about them!

A list of Zones where the Custom Role will be able to spawn.\
The spawn room will be chosen randomly.

### Spawn Rooms

**Configuration element name:** `spawn_rooms` \
**Type:** [`[]RoomType`](../../syntax-notions/enums.md#roomtype)&#x20;

**This configuration value contains Enum values**: please visit the [Enums](../../syntax-notions/enums.md) page in order to learn more about them!

A list of Rooms where the Custom Role will be able to spawn.\
The spawn room will be chosen randomly between the given values.

### Spawn Roles

**Configuration element name:** `spawn_roles` \
**Type:** [`[]RoleTypeId`](../../syntax-notions/enums.md#roletypeid-and-team)

**This configuration value contains Enum values**: please visit the [Enums](../../syntax-notions/enums.md) page in order to learn more about them!

The Custom Role will spawn in one of this Role list random spawn point.

### Spawn Points

**Configuration element name:** `spawn_points` \
**Type:** `[]string`&#x20;

A list of Spawn Points where the role will be able to spawn.\
In order to read more about Spawn Points please visit [this page](../../commands/spawnpoint/).

### Required Permission

**Configuration element name:** `spawn_points` \
**Type:** `string` or `[]string`

A "custom" LabApi permission or Base Game permission that the player **must** have in order to natually spawn as this Custom Role.\
For example if you put `ucr.vip.role1` then the people with these perms will be able to spawn as this Custom Role:\
\- `*`\
\- `*.*`\
\- `ucr.*`\
\- `ucr.vip.*`\
\- `ucr.vip.role1`
