---
icon: flag-swallowtail
---

# Vanilla Flags

**UCR** comes with some hard-coded "**Vanilla Custom Flags**" and they are the following ones:

## AmnesiaResistance

The **AmnesiaResistance** flag disallows the player to get **AmnesiaVision** or **AmnesiaItems** effect.

## ColorfulNickname

The **ColorfulNickname** will change the color of the nickname of the Custom Role's player(s) inside the player infobox.

It requires a param named `color` which must be one of these colors: [infoarea-colors.md](../../../syntax-notions/infoarea-colors.md "mention")

## ColorfulRaName

The **ColorfulRaName** will change the color of the nickname of the Custom Role's player(s) inside the RemoteAdmin player list.

It requires a param named `color` which can be any hex (like `#ff00ff`).

## CustomInfoOrder

The **CustomPermissions** flag allows to change the CustomInfo's order to your liking.

Example of usage:

```yaml
custom_flags:
- CustomInfoOrder:
    order: "%custominfo%%nickname%%rolename%"
```

**Note:** These are the 3 Placeholders: <kbd>%custominfo%</kbd>, <kbd>%nickname%</kbd> and <kbd>%rolename%</kbd>

## CustomPermissions

The **CustomPermissions** flag allows the player that has the Custom Role to have additional LabApi permissions.

Example of usage:

```yaml
custom_flags:
- CustomPermissions:
    permissions: "ucr.spawn, ucr.list"
```

**Note:** you can also put a single permission

## CustomScpAnnouncer

The **CustomScpAnnouncer** flag will force the game to make an announcement about the termination of this Custom Role, whether is an SCP or not.

It requires a param named `name` where you have to put the SCP number.

Example of usage:

```yaml
custom_flags:
- CustomScpAnnouncer:
    name: 'SCP-250'
```

This will make the game say "SCP-250".

## DoNotTriggerScp096

The **DoNotTriggerScp096** Custom Flag will simply allow the Custom Role to directly watch SCP-096 without triggering the rage.

## DoNotTriggerTeslaGates

The **DoNotTriggerTeslaGates** will disable the Tesla Gate activation for this Custom Role.

**Note:** if there's another person that CAN activate the Tesla Gate then it WILL activate, no matter what.

## DropItemOnDeath

The **DropItemOnDeath** allows you to make the Custom Role drop a specific item when they die.

It requires a param named `item` where you have to put the wanted [ItemType](../../../syntax-notions/enums.md#itemtype).

Example of usage:

```yaml
custom_flags:
- DropItemOnDeath:
    item: Adrenaline
```

## DropNothingOnDeath

The **DropNothingOnDeath** will destroy every item dropped by the Custom Role when they die.

## FullCandyBag

The **FullCandyBag** will spawn (when the Custom Role spawns) a Candy Bag in the player's inventory with inside how many candies you want.

It requires a param named `candies` who's a [List](../../../commands/list.md) of [`CandyKindIDs`](../../../syntax-notions/enums.md#candykindid) .\
Example:

```yaml
custom_flags:
- FullCandyBag:
    candies:
    - Rainbow
    - Yellow
    - Blue
```

## ItemBan

The **ItemBan** Custom Flag will prevent the Custom Role from picking up a specific [Item](../../../syntax-notions/enums.md#itemtype).

It requires a param named `item_type` where you have to put the wanted [ItemType](../../../syntax-notions/enums.md#itemtype).

Example of usage:

```yaml
custom_flags:
- ItemBan:
    item_type: Coin
```

**Note:** if you need to ban more than a single item you **can add as many ItemBan custom flags as you want!**

```yaml
custom_flags:
- ItemBan:
    item_type: Coin
- ItemBan:
    item_type: Radio
```

## KeepInventoryOnEscape

The **KeepInventoryOnEscape** flag will allow the player to carry his item through escape.\
The <kbd>drop</kbd> argument is optional.

Example of usage:

```yaml
custom_flags:
- KeepInventoryOnEscape:
    drop: true
OR
custom_flags:
- KeepInventoryOnEscape
```

## **LifeStealer**

The **LifeStealer** Custom Flag will allow the Custom Role to gain a certain number of HP when they deal damage to other players.

It requires a param named `percentage` who's an `int32` and it represent the percentage of the damage that will be transferred to the Custom Role.\
For example, if `percentage: 50` and the Custom Role deals a `100HP` damage they will be healed with `50HP`.

Example of usage:

```yaml
custom_flags:
- LifeStealer:
    percentage: 75
```

## NotAffectedByAppearance

The **NotAffectedByAppearance** is a simple Custom Flag that will prevent the user from seeing the "fake" appearance of every other Custom Role and they instead will see their real role.

## PacifismUntilDamage

The **PacifismUntilDamage** is a simple Custom Flag that will prevent the user from being damaged as long as he doesn't damage anyone.

## **Schematic**

The **Schematic** Custom Flag will spawn the specified [**ProjectMER**](https://github.com/Michal78900/ProjectMER) schematic and attach it to the player.

[**ProjectMER**](https://github.com/Michal78900/ProjectMER) needed to be install to work with this CustomModule.

It requires a param <kbd>name</kbd>, here you need to set the **Schematics** name.

Example of usage:

```yaml
custom_flags:
- Schematic:
    name: hat
```

## SilentAnnouncer

The **SilentAnnouncer** Custom Flag will prevent the game from making the SCP termination announcement for that Custom Role.

## SilentWalker

The **SilentWalker** Custom Flag will prevent the Custom Role from making walking noises.

## TutorialRagdoll

The **TutorialRagdoll** Custom Flag will spawn a Tutorial role ragdoll when they die instead of their old role ragdoll.

## **Wardobe**

The **Wardobe** Custom Flag will spawn the specified [**ProjectMER**](https://github.com/Michal78900/ProjectMER) schematic and attach it using [SLWardobe](https://github.com/ChochoZagorski/SLWardrobe/).

[**ProjectMER**](https://github.com/Michal78900/ProjectMER) and [SLWardobe](https://github.com/ChochoZagorski/SLWardrobe/) needed to be install to work with this CustomModule.

It requires a param <kbd>name</kbd>, here you need to set the **Wardobe** name.

Example of usage:

```yaml
custom_flags:
- Wardobe:
    name: hat
```
