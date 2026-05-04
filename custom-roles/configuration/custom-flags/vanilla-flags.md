---
icon: flag-swallowtail
---

# Vanilla Flags

**UCR** comes with some hard-coded "**Vanilla Custom Flags**" and they are the following ones:

## AmnesiaResistance

The **AmnesiaResistance** flag disallows the player to get **AmnesiaVision** or **AmnesiaItems** effect.

## ChangeAppearanceOnKill

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

**Note:** These are the 3 Placeholders: `%custominfo%`, `%nickname%` and `%rolename%`

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

It requires a param named `item_type` who's a [List](../../../commands/list.md) or a `string` of [ItemType](../../../syntax-notions/enums.md#itemtype).

If you put `SCP330` it will also prevent the player from interacting with SCP-330's bowl.

Example of usage:

```yaml
custom_flags:
- ItemBan:
    item_type: Coin
OR
custom_flags:
- ItemBan:
    item_type:
    - Medkit
    - Coin
    - SCP500
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

## Wardrobe

The **Wardrobe** Custom Flag will spawn the specified [**ProjectMER**](https://github.com/Michal78900/ProjectMER) schematic and attach it using [SLWardrobe](https://github.com/ChochoZagorski/SLWardrobe/).

[**ProjectMER**](https://github.com/Michal78900/ProjectMER) and [SLWardrobe](https://github.com/ChochoZagorski/SLWardrobe/) needed to be install to work with this CustomModule.

It requires a param <kbd>name</kbd>, here you need to set the **Wardrobe** name.

Example of usage:

```yaml
custom_flags:
- Wardrobe:
    name: hat
```

## CustomKeycard

The **CustomKeycard** Custom Flag spawns a fully customized keycard and gives it to the player upon spawn. It supports four distinct keycard visual templates, each with their own configurable parameters such as colors, labels, permissions, and wear state.

***

### Required parameters

| Parameter     | Type       | Description                                                                       |
| ------------- | ---------- | --------------------------------------------------------------------------------- |
| `KeycardType` | `ItemType` | The keycard variant to spawn. Must be one of the customizable types listed below. |

***

### Optional parameters

| Parameter          | Type                  | Default          | Description                                                    |
| ------------------ | --------------------- | ---------------- | -------------------------------------------------------------- |
| `ItemName`         | `string`              | `Custom Keycard` | The in-game display name of the keycard item.                  |
| `HolderName`       | `string`              | `Unknown`        | The name printed on the card as the holder.                    |
| `CardLabel`        | `string`              | _(empty)_        | Secondary label text shown on the card body.                   |
| `Permissions`      | `DoorPermissionFlags` | `None`           | Door access permissions granted by the keycard.                |
| `KeycardColor`     | `Color` (hex)         | `#FFFFFF`        | Primary background color of the keycard.                       |
| `PermissionsColor` | `Color` (hex)         | `#FFFFFF`        | Color of the permissions indicator stripe.                     |
| `LabelColor`       | `Color` (hex)         | `#FFFFFF`        | Color of the label text.                                       |
| `WearLevel`        | `byte`                | `0`              | Visual wear/damage level of the card.                          |
| `SerialLabel`      | `string`              | `000000000000`   | Serial number printed on the card.                             |
| `RankIndex`        | `int`                 | `0`              | Rank insignia index shown on the card. TaskForce variant only. |

***

### Supported keycard types

The `KeycardType` parameter must be set to one of the following `ItemType` values. Each variant has a different set of applicable parameters.

| KeycardType               | Supported parameters                                                                                                               |
| ------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| `KeycardCustomManagement` | `ItemName`, `CardLabel`, `Permissions`, `KeycardColor`, `PermissionsColor`, `LabelColor`                                           |
| `KeycardCustomMetalCase`  | `ItemName`, `HolderName`, `CardLabel`, `Permissions`, `KeycardColor`, `PermissionsColor`, `LabelColor`, `WearLevel`, `SerialLabel` |
| `KeycardCustomSite02`     | `ItemName`, `HolderName`, `CardLabel`, `Permissions`, `KeycardColor`, `PermissionsColor`, `LabelColor`, `WearLevel`                |
| `KeycardCustomTaskForce`  | `ItemName`, `HolderName`, `Permissions`, `KeycardColor`, `PermissionsColor`, `SerialLabel`, `RankIndex`                            |

Passing a non-customizable `ItemType` (e.g. `KeycardO5`) will cause the module to log an error and skip keycard creation entirely. No keycard will be given to the player.

***

### Permissions

The `Permissions` parameter accepts one or more `DoorPermissionFlags` values separated by commas. Internally these are mapped to three independent categories, each with levels 0–3. **Levels are cumulative within a category** — specifying a higher level implicitly includes all lower levels of that category.

#### Available flags

| Flag                    | Description                                      |
| ----------------------- | ------------------------------------------------ |
| `None`                  | No permissions.                                  |
| `All`                   | Grants all permissions.                          |
| `Checkpoints`           | Access to checkpoint doors. Admin level 1.       |
| `ExitGates`             | Access to surface exit gates. Admin level 2.     |
| `Intercom`              | Access to intercom. Admin level 1.               |
| `AlphaWarhead`          | Access to alpha warhead controls. Admin level 3. |
| `ContainmentLevelOne`   | Containment level 1 doors.                       |
| `ContainmentLevelTwo`   | Containment level 2 doors.                       |
| `ContainmentLevelThree` | Containment level 3 doors.                       |
| `ArmoryLevelOne`        | Armory level 1 doors.                            |
| `ArmoryLevelTwo`        | Armory level 2 doors.                            |
| `ArmoryLevelThree`      | Armory level 3 doors.                            |
| `ScpOverride`           | Allows opening SCP-locked doors.                 |

Containment and Armory levels are cumulative within their category — `ContainmentLevelTwo` internally covers level 1 as well, so specifying both is redundant. Admin flags (`Checkpoints`, `Intercom`, `ExitGates`, `AlphaWarhead`) and `ScpOverride` are independent and can be combined freely.

#### Example

```yaml
Permissions: ContainmentLevelTwo, ArmoryLevelOne, ExitGates
```

This grants Containment level 2, Armory level 1, and Admin level 2 (Exit Gates).

***

### Color format

All color parameters accept a hex color string. The leading `#` is optional — both `#FF0000` and `FF0000` are valid.

***

### Example usage

#### Management keycard

```yaml
custom_flags:
  - CustomKeycard:
      KeycardType: KeycardCustomManagement
      ItemName: Senior Researcher Card
      CardLabel: Research Division
      Permissions: Checkpoints
      KeycardColor: "#1A3A5C"
      PermissionsColor: "#4A90D9"
      LabelColor: "#FFFFFF"
```

#### Metal case with wear

```yaml
custom_flags:
  - CustomKeycard:
      KeycardType: KeycardCustomMetalCase
      ItemName: Field Agent Card
      HolderName: Agent Smith
      CardLabel: Mobile Task Forces
      Permissions: Checkpoints, ContainmentLevelOne
      KeycardColor: "#2C2C2C"
      PermissionsColor: "#FF6600"
      LabelColor: "#CCCCCC"
      WearLevel: 3
      SerialLabel: MTF-EPSILON-11
```

#### Task Force keycard with rank

```yaml
custom_flags:
  - CustomKeycard:
      KeycardType: KeycardCustomTaskForce
      ItemName: Commander Card
      HolderName: Commander Davis
      Permissions: ArmoryLevelTwo, Checkpoints
      KeycardColor: "#1C3A1C"
      PermissionsColor: "#33AA33"
      SerialLabel: NTF-EPSILON-01
      RankIndex: 2
```
