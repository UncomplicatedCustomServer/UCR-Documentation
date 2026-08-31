---
icon: flag-swallowtail
---

# Vanilla Flags

**UCR** comes with some hard-coded "**Vanilla Custom Flags**" and they are the following ones:

## AmnesiaResistance

The **AmnesiaResistance** flag disallows the player to get **AmnesiaVision** or **AmnesiaItems** effect.

## ChangeAppearanceOnKill

## ColorfulNickname

{% hint style="danger" %}
<mark style="color:$danger;">This module is deprecated and will be removed in a future version. Use</mark> [<mark style="color:$danger;">InfoTag</mark>](vanilla-flags.md#infotag) <mark style="color:$danger;">instead.</mark>
{% endhint %}

The **ColorfulNickname** will change the color of the nickname of the Custom Role's player(s) inside the player infobox.

It requires a param named `color` which must be one of these colors: [infoarea-colors.md](../../../syntax-notions/infoarea-colors.md "mention")

## ColorfulRaName

The **ColorfulRaName** will change the color of the nickname of the Custom Role's player(s) inside the RemoteAdmin player list.

It requires a param named `color` which can be any hex (like `#ff00ff`).

## CustomInfoOrder&#x20;

{% hint style="danger" %}
<mark style="color:$danger;">This module is deprecated and will be removed in a future version. Use</mark> [<mark style="color:$danger;">InfoTag</mark>](vanilla-flags.md#infotag) <mark style="color:$danger;">instead.</mark>
{% endhint %}

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

### CustomTeam

The **CustomTeam** flag lets you group Custom Roles into an custom team, identified by a string `team` name. Players whose roles carry a `CustomTeam` with the same (case-insensitive) team name are treated as teammates: they **cannot damage, flashbang or otherwise harm each other**, exactly like members of a vanilla team.

It requires a param named `team` which must be a non-empty string.

Example of usage:

```yaml
custom_flags:
- CustomTeam:
    team: SerpentsHand
```

Any two roles (or the same role reused by multiple players) that set `team: SerpentsHand` are now teammates towards each other. A different role using `team: RapidResponseTeam` is a separate team and can freely fight both the `SerpentsHand` and everyone else.

The `team` is just a label — it is not a real game `Team` value, does not change the base `Team` of the player.

## DoNotTrigger096

The **DoNotTrigger096** Custom Flag will simply allow the Custom Role to directly watch SCP-096 without triggering the rage.

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

## InfoTag

The **InfoTag** flag is a single, unified custom flag that controls **everything** shown on a Custom Role's Custom Info — the order of the parts, each part's colour and bold style, and the MTF unit name. It replaces the older `CustomInfoOrder` and `ColorfulNickname` flags: those still work on their own, but if a role also has an `InfoTag`, the `InfoTag` takes full control of the Custom Info.

The tag is built from four tokens: `%custominfo%`, `%nickname%`, `%rolename%` and `%unitname%`. Two tokens written back-to-back (`%a%%b%`) are placed on separate lines; put a literal space (or any other text) between them to keep them on the same line.

| Token          | Filled from                                                  | Notes                                                                                                                                                                              |
| -------------- | ------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `%nickname%`   | the role's `nickname` field                                  | [Placeholders](../placeholders.md) are resolved (e.g. `D-%dnumber%`), then used as both the player's display name and this line. Empty → falls back to the player's real nickname. |
| `%custominfo%` | the role's `custom_info` field                               | Free text, [placeholders](../placeholders.md) resolved. Empty → the line is skipped entirely.                                                                                      |
| `%rolename%`   | `name` or the base `role`, depending on `override_role_name` | `override_role_name: true` shows the custom `name` (e.g. `Janitor`). `false` shows the base `role`'s real in-game name (e.g. `Class-D Personnel`).                                 |
| `%unitname%`   | the game's MTF unit naming                                   | Only applies to `FoundationForces`; rendered with `unit_format` (default `({unit})`). Set `show_unitname: false` to hide it.                                                       |

#### Parameters

* `order` (`string`, default `"%custominfo%%nickname%%rolename% %unitname%"`) — the layout of the four tokens described above.
* `custominfo_color`, `nickname_color`, `rolename_color`, `unitname_color` (`string`, optional) — per-part colour. Accepts a friendly name (`pink`, `red`, `pumpkin`, `green`, ...) or a hex code; only the 24 colours the game allows on a name tag are valid (same palette used by `badge_color`).
* `custominfo_bold`, `nickname_bold`, `rolename_bold`, `unitname_bold` (`bool`, default `false`) — bolds that part.
* `unit_format` (`string`, default `"({unit})"`) — how the MTF unit name is rendered; `{unit}` is replaced with the unit name. Square brackets (`[` `]`) are not allowed.
* `show_unitname` (`bool`, default `true`) — hides `%unitname%` entirely when `false`.
* `show_badge` (`bool`, default `true`) — shows/hides the badge/rank line the game renders itself. Its colour is still controlled by the role's `badge_color`, not by `InfoTag`.
* `show_powerstatus` (`bool`, default `true`) — shows/hides power status line.

Example of usage:

```yaml
custom_flags:
- InfoTag:
    # Layout. Default: "%custominfo%%nickname%%rolename% %unitname%"
    order: "%rolename% %unitname%%nickname%%custominfo%"
    # Per-part colours: a name (pink, red, pumpkin, green, ...) or an accepted hex.
    rolename_color: red
    nickname_color: green
    unitname_color: yellow
    custominfo_color: white
    # Per-part bold
    rolename_bold: true
    nickname_bold: false
    # MTF unit name rendering ({unit} is the placeholder). Square brackets are not allowed.
    unit_format: "({unit})"
    show_unitname: true
    # Other name-tag elements (can be hidden, not recoloured here):
    show_badge: true          # the badge (its colour = the role's badge_color)
    show_powerstatus: true    # the power status line
```

**Note:** An empty token never leaves a blank line, so parts can be freely reordered or omitted from `order` without leaving gaps.

### Migration from CustomInfoOrder/ColorfulNickname

Roles that still use `CustomInfoOrder`, `ColorfulNickname` or `NoUnitName` are **automatically migrated at load** into an equivalent `InfoTag` (in memory), so they keep working and look exactly the same. Each migrated role logs a warning listing the deprecated flags and prints a ready-to-paste `InfoTag` replacement.

To persist the migration to the role's YAML file, run `ucr update <id>` (or `ucr update all`) — the same command used to upgrade outdated role files. Code-registered roles (no YAML file) are migrated in memory only, and a `reload` re-runs the migration from the original files.

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

## NoUnitName

{% hint style="danger" %}
<mark style="color:$danger;">This module is deprecated and will be removed in a future version. Use</mark> [<mark style="color:$danger;">InfoTag</mark>](vanilla-flags.md#infotag) <mark style="color:$danger;">instead.</mark>
{% endhint %}

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

The `ItemName`, <kbd>HolderName</kbd> and <kbd>CardLabel</kbd> supports [Placeholders](../placeholders.md).

***

### Required parameters

| Parameter     | Type       | Description                                                                       |
| ------------- | ---------- | --------------------------------------------------------------------------------- |
| `KeycardType` | `ItemType` | The keycard variant to spawn. Must be one of the customizable types listed below. |

***

### Optional parameters

<table><thead><tr><th width="195">Parameter</th><th width="189">Type</th><th width="177">Default</th><th width="187">Description</th></tr></thead><tbody><tr><td><code>ItemName</code></td><td><code>string</code></td><td><code>Custom Keycard</code></td><td>The in-game display name of the keycard item.</td></tr><tr><td><code>HolderName</code></td><td><code>string</code></td><td><code>Unknown</code></td><td>The name printed on the card as the holder.</td></tr><tr><td><code>CardLabel</code></td><td><code>string</code></td><td><em>(empty)</em></td><td>Secondary label text shown on the card body.</td></tr><tr><td><kbd>ContainmentLevel</kbd></td><td><kbd>int</kbd></td><td>0</td><td>The Containment permission's level.</td></tr><tr><td><kbd>ArmoryLevel</kbd></td><td><kbd>int</kbd></td><td>0</td><td>The Armory permission's level.</td></tr><tr><td><kbd>AdminLevel</kbd></td><td><kbd>int</kbd></td><td>0</td><td>The Admin permission's level.</td></tr><tr><td><code>Permissions</code></td><td><code>DoorPermissionFlags</code></td><td><code>None</code></td><td>Door access permissions granted by the keycard.</td></tr><tr><td><code>KeycardColor</code></td><td><code>Color</code> (hex)</td><td><code>#FFFFFF</code></td><td>Primary background color of the keycard.</td></tr><tr><td><code>PermissionsColor</code></td><td><code>Color</code> (hex)</td><td><code>#FFFFFF</code></td><td>Color of the permissions indicator stripe.</td></tr><tr><td><code>LabelColor</code></td><td><code>Color</code> (hex)</td><td><code>#FFFFFF</code></td><td>Color of the label text.</td></tr><tr><td><code>WearLevel</code></td><td><code>byte</code></td><td><code>0</code></td><td>Visual wear/damage level of the card.</td></tr><tr><td><code>SerialLabel</code></td><td><code>string</code></td><td><code>000000000000</code></td><td>Serial number printed on the card.</td></tr><tr><td><code>RankIndex</code></td><td><code>int</code></td><td><code>0</code></td><td>Rank insignia index shown on the card. TaskForce variant only.</td></tr></tbody></table>

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
