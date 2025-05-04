---
icon: bars-staggered
---

# Configuration elements

Here the main configuration elements will be explained.\
You need to read the whole page in order to create basic Custom Roles with UCR.\
We'll always reference to the main YAML configuration given at the [Configuration](./) part of this wiki.

## Role ID

**Configuration element name:** `id` \
**Type:** `int32`&#x20;

The unique Identifier for your Custom Role.\
You'll have to use this in order to spawn a player as that role and to get information about that role.\
Identifiers **must** be unique so watch out to avoid using the same Id for multiple roles: only the first one will be loaded!

## Role Name

**Configuration element name:** `name` \
**Type:** `string`&#x20;

The name of the Custom Role.\
This value is visible only to the server owner (unless [Override Role Name](configuration-elements.md#override-role-name) is activated) and it can be a simpler way to identify a role.\
If [Override Role Name](configuration-elements.md#override-role-name) is activated then this string will appear also to the other players instead of the vanilla role name.

## Override Role Name

**Configuration element name:** `override_role_name` \
**Type:** `bool`&#x20;

Whether the [Role Name](configuration-elements.md#role-name) should appear inside the player info area (to other players) instead of the vanilla role name.

## Nickname

**Configuration element name:** `nickname` \
**Type:** `string`&#x20;

**This configuration value is nullable** and if null no operations will be done on the player's nickname.

The nickname that will be assigned to the player when they'll be this Custom Role.\
You can **put different nicknames** by splitting them with a comma (`,`): if there are multiple nicknames the plugin will randomly choose between one of them.

That function supports also Placeholders(R).

## Custom Info

**Configuration element name:** `custom_info` \
**Type:** `string`&#x20;

**This configuration value is nullable** and if null nothing will be set as the player's custom info.

The custom info that will be assigned to the player when they'll be this Custom Role.\
Custom info appears just under the role name and it's visible only to other players.

## Badge Name

**Configuration element name:** `badge_name` \
**Type:** `string`&#x20;

**This configuration value is nullable** and if null no operations no badge will be added to the player.

The temporary Badge that will be added to the player when they'll be this Custom Role.\
Badges are visible both to the player and to other players in the custom info area (it will be the first element) and in the player list.

You can choose a color for the badge by editing [Badge Color](configuration-elements.md#badge-color)

## Badge Color

**Configuration element name:** `badge_name` \
**Type:** `string*`&#x20;

**This configuration value is nullable** and if null no operations no badge will be added to the player

The Badge color.\
**Note:** you can use a limited number of colors marked as "Server groups" inside the [Official NW color list](https://web.archive.org/web/20230315023448/https://en.scpslgame.com/index.php?title=Docs:Permissions#Colors)!

## Role

**Configuration element name:** `role` \
**Type:** [`RoleTypeId`](../../c-notions/enums.md#roletypeid-and-team)&#x20;

**This configuration value is an Enum**: please visit the [Enums](../../c-notions/enums.md) page in order to learn more about them!

The wanted **RoleTypeId** for the Custom Role.

## Team

**Configuration element name:** `team` \
**Type:** [`Team`](../../c-notions/enums.md#roletypeid-and-team)&#x20;

**This configuration value is nullable** and if null the player will have the default team of the choosen [Role](configuration-elements.md#role).

**This configuration value is an Enum**: please visit the [Enums](../../c-notions/enums.md) page in order to learn more about them!

The custom team for a Custom Role.\
You can create, for example, a `ClassD` that's an `SCPs` or things like that to make the game more interesting.

## Role Appearance

**Configuration element name:** `role_appearance`\
**Type:** [`RoleTypeId`](../../c-notions/enums.md#roletypeid-and-team)&#x20;

**This configuration value is nullable** and if null the player will have the default appearance of the choosen [Role](configuration-elements.md#role).

**This configuration value is an Enum**: please visit the [Enums](../../c-notions/enums.md) page in order to learn more about them!

If not null the player will be the given [Role](configuration-elements.md#role) but every other player will see him as the given Role Appearance role.

## Is Friend Of

**Configuration element name:** `is_friend_of`\
**Type:** [`[]Team`](../../c-notions/enums.md#roletypeid-and-team)

**This configuration value contains Enum values**: please visit the [Enums](../../c-notions/enums.md) page in order to learn more about them!

With **Is Friend Of** you can decide which teams can harm (and can be harmed) by this Custom Role.\
For example, if the Custom Role's role is `ClassD` and is friend of is

```yaml
is_friend_of:
- Scientists
```

the Custom Role won't be able to damage Scientists (nor them will be able to harm the Custom Role).

**Note:** this is just an **ADDICTION** to the game main logic!

## Health

The **Health** configuration parameter has its own object with its own specifications.\
Please visit [this page](health-and-ahp.md#health) in order to read how to configure it.

## AHP

The **AHP** configuration parameter has its own object with its own specifications.\
Please visit [this page](health-and-ahp.md#artificial-health-ahp) in order to read how to configure it.

## Hume Shield

The **Hume Shield** configuration parameter has its own object with its own specifications.\
Please visit [this page](hume-shield.md) in order to read how to configure it.

## Effects

The **Effects** configuration parameter has its own object with its own specifications.\
Please visit [this page](effects.md) in order to read how to configure it.

## Stamina

The **Stamina** configuration parameter has its own object with its own specifications.\
Please visit [this page](stamina.md) in order to read how to configure it.

## Max SCP-330 Candies

**Configuration element name:** `max_scp330_candies` \
**Type:** `int32`&#x20;

Indicates the maximum number of candies that can be taken from **SCP-330** without having your hands severed.

## Can Escape

**Configuration element name:** `can_escape` \
**Type:** `bool`&#x20;

Indicates whether the Custom Role can escape or not (through the exit on the Surface).\
The behavior behind the escape event is decided by editing the [Role After Escape](configuration-elements.md#role-after-escape) configuration parameter.

## Role After Escape

The **Role After Escape** configuration parameter has a complex syntax in order to allow server-owners to have a more advanced and complete configuration method to customize escape logic for each Custom Role.\
Please visit [this page](escape-logic.md) in order to learn the syntax and read how to correctly use it.

## Scale

**Configuration element name:** `scale` \
**Type:** `Vector3`&#x20;

A simple `Vector3` that decide the scale on the three dimensions (X, Y and Z).\
It's an object with three keys (x, y and z) and three `int32` as values.\
Example:

```yaml
scale:
  x: 1
  y: 2
  z: 1
```

## Spawn Broadcast

**Configuration element name:** `spawn_broadcast` \
**Type:** `string`&#x20;

The spawn broadcast that gets displayed to the user when they spawn as the Custom Role.\
Here you can use the Unity syntax to decide the text's size, color, weight and everything else.

You can choose the duration through the [Spawn Broadcast Duration](configuration-elements.md#spawn-broadcast-duration) configuration value.

## Spawn Broadcast Duration

**Configuration element name:** `spawn_broadcast_duration` \
**Type:** `ushort`&#x20;

The duration of the spawn broadcast in seconds.

## Spawn Hint

**Configuration element name:** `spawn_hint` \
**Type:** `string`&#x20;

The spawn hint that gets displayed to the user when they spawn as the Custom Role.\
Here you can use the Unity syntax to decide the text's size, color, weight and everything else.

You can choose the duration through the [Spawn Hint Duration](configuration-elements.md#spawn-hint-duration) configuration value.

## Spawn Hint Duration

**Configuration element name:** `spawn_hint_duration` \
**Type:** `float`&#x20;

The duration of the spawn hint in seconds.

## Custom Inventory Limits

**Configuration element name:** `custom_inventory_limits` \
**Type:** [`ItemCategory`](../../c-notions/enums.md#itemcategory), `sbyte`&#x20;

**This configuration value contains Enum values**: please visit the [Enums](../../c-notions/enums.md) page in order to learn more about them!

A simple Dictionary that allow server owners to edit the default inventory limits value for each Custom Role.\
For example Class-D have a limit of 3 firearms: with this configuration parameter you can increase or even decrease this value!\
**Note:** if an ItemCategory is not specified the plugin will use it's default value!

Example:

```yaml
custom_inventory_limits:
  Firearm: 1
  Grenade: 5
```

_(Yeah now you can have up to 5 grenades but only 1 firearm)_

## Inventory

**Configuration element name:** `inventory` \
**Type:** [`[]ItemTypeId`](../../c-notions/enums.md#itemtype)&#x20;

**This configuration value contains Enum values**: please visit the [Enums](../../c-notions/enums.md) page in order to learn more about them!

Customizing the inventory of a Custom Role might be the most important thing to do and UCR give you a simple -but powerful- tool to achieve that.\
The **Inventory** configuration value is a simple list of ItemTypes: every item will be added to the player's inventory.

Example:

```yaml
inventory:
- Flashlight
- KeycardJanitor
```

## Custom Items Inventory

**Configuration element name:** `custom_items_inventory` \
**Type:** `[]int32`&#x20;

UCR does support both **EXILED CustomItems** and **UncomplicatedCustomItems** (UCI) and with this configuration parameter you can add Custom Items from both plugins to your Custom Role.\
Just put the Custom Item's Id and it will be given!\
**Note:** remember to NOT have Id conflicts between EXILED CI and UCI as if you have two items with the same Id UCR will always take the UCI one!

Example:

```yaml
custom_items_inventory:
- 2
- 5
```

## Ammo

**Configuration element name:** `ammo` \
**Type:** [`[]AmmoType`](../../c-notions/enums.md#ammotype)

**This configuration value contains Enum values**: please visit the [Enums](../../c-notions/enums.md) page in order to learn more about them!

You can also customize the number of ammos that a Custom Roles has.\
**Note:** the plugin actually overrides the default number of ammos: for that reason if you don't give ammos to a Custom Role it won't have **any** of them!

## Damage Multiplier

**Configuration element name:** `damage_multiplier` \
**Type:** `float`&#x20;

The damage multiplier that will be applied to the damage dealt by **this role** to another player.\
We use the following formula:

```
newDamage = oldDamage * damage_multiplier
```

For that reason if the value is `1` then nothing will change while if we set the value for example to `1.5` and we deal `20HP` the given damage will be `30HP`.

## Spawn Settings

The **SpawnSettings** configuration parameter has its own object as it's a main part of the configuration and because of his complexity another page is needed for a better organization.\
Please visit this page in order to read more about the Spawn Settings param.

## Custom Flags

With the `v6.0.0` **Custom Flags** officially became open to the developers and because of that the system changed in a more customizable -but complex- one.\
The explanation (with the list of built-in Custom Flags) is available in this page.

## Ignore Spawn System

**Configuration element name:** `ignore_spawn_system` \
**Type:** `bool`&#x20;

If true the Custom Role won't be evaluated by our Spawn System but you'll be able to spawn it manually using commands!
