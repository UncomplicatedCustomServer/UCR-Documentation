---
icon: hand-holding-medical
---

# Spawn

If you need to spawn manually a Custom Role you can use the **Spawn** command.

### Syntax

```
ucr spawn <Player Id or Name> <Role Id> (method)
```

### Permission

```
ucr.spawn
```

### Description

With this command you can spawn **one or more player** as a Custom Role.

The method parameter allows you to decide if spawn the role synchronously or asynchronously.\
If you need to spawn it **synchronously** then put `sync` as method.

### Player pointers

There are different pointers that you can use to point a single player, a defined group of player or everyone.

If you put **a simple player id or name** then only the selected player will be spawned as the Custom Role.

If you put **different player ids, divided by a comma** (`,`) then these players will be spawned as the Custom Role.

If you put `all` then every player in the server will be spawned as the Custom Role.

If you put `spectators` or `spect` then only the spectators will be spawned as the Custom Role.

If you put `alive` or `al` then only the alives will be spawned as the Custom Role.
