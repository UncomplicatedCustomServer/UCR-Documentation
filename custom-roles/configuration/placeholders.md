---
icon: brackets-curly
---

# Placeholders

**Placeholders** are `%name%` tokens you can put inside certain text fields of a Custom Role; UCR replaces them with a live value (the player's real nickname, a random D-class number, the player's current health, ...) every time that text is shown.

#### Where you can use them

| Field                                                        | Supports placeholders?    |
| ------------------------------------------------------------ | ------------------------- |
| `nickname`                                                   | ✅                         |
| `custom_info`                                                | ✅                         |
| `ucr custominfo <player> <text>` command                     | ✅                         |
| `CustomKeycard` flag's `ItemName`, `HolderName`, `CardLabel` | ✅                         |
| `spawn_broadcast`                                            | ❌ (shown as literal text) |
| `spawn_hint`                                                 | ❌ (shown as literal text) |
| `badge_name`                                                 | ❌ (shown as literal text) |

Any `%...%` token used in a field that doesn't support placeholders is shown to players exactly as typed, instead of being replaced.

#### Available placeholders

| Placeholder                 | Replaced with                                                                                              |
| --------------------------- | ---------------------------------------------------------------------------------------------------------- |
| `%nick%`                    | The player's real, unmodified nickname.                                                                    |
| `%displayname%`             | The current name of the player — their custom `nickname`, otherwise the same as `%nick%`.                  |
| `%rand%`                    | A random whole number between 0 and 9.                                                                     |
| `%dnumber%`                 | A random whole number between 1000 and 9999 — handy for `D-%dnumber%` style nicknames.                     |
| `%unitid%`                  | The player's unit number (e.g. the `4` in `Tango-4`).                                                      |
| `%unitname%`                | The player's full generated unit name (e.g. `Tango-7`), if their team has one this round; otherwise empty. |
| `%rolename%`                | The real in-game name of the player's current base role (e.g. `Class-D Personnel`).                        |
| `%customrolename%`          | The custom role's `name` field.                                                                            |
| `%customroleid%`            | The custom role's numeric `id`.                                                                            |
| `%customrolebadge%`         | The custom role's `badge_name` field.                                                                      |
| `%health%` / `%max_health%` | The player's current / maximum health.                                                                     |
| `%ahp%` / `%max_ahp%`       | The player's current / maximum Additional Human Process (AHP) shield.                                      |
| `%hume%` / `%max_hume%`     | The player's current / maximum Hume shield.                                                                |

All placeholders are re-evaluated every time the text is rendered (for example, `%health%` in a `custom_info` always shows the player's _current_ health, not their health at spawn time). `%rand%` and `%dnumber%` are re-rolled on every evaluation too, so avoid them if you want a number that stays fixed for the round — generate it once yourself and put it in `custom_info` directly instead.

#### Examples

```yaml
# A random D-class-style nickname
nickname: "D-%dnumber%"
```

```yaml
# Custom info showing the player's real nickname and current health
custom_info: "%nick%\n<color=red>HP: %health%/%max_health%</color>"
```

```yaml
custom_flags:
- CustomKeycard:
    ItemName: "%customrolebadge% Keycard"
    HolderName: "%nick%"
```

#### Notes

* Placeholders are matched exactly as written, lowercase, between two `%` characters — `%Nick%` or `%NICK%` will **not** be replaced.
* An unknown placeholder (a typo, or one not in the table above) is left in the text as-is instead of causing an error — double-check spelling if a `%...%` shows up literally in-game.
* `%unitid%` and `%unitname%` are only meaningful for `FoundationForces` roles; on any other team they resolve to an empty value.
