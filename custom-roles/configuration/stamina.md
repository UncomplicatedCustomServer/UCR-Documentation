---
icon: person-running-fast
---

# Stamina

The **Stamina** decides how much you can run.\
With UCR you can customize every aspect of it, in order to create an even more custom server!

The **Stamina** object should look like this:

```yaml
stamina:
  regen_multiplier: 1
  usage_multiplier: 1
  infinite: false
```

### Regeneration Multiplier

**Configuration element name:** `regen_multiplier` \
**Type:** `float`&#x20;

The multiplier of the amout of Stamina that is regenerated to the player every second.\
The formula we use is

```
newStaminaRegen = staminaRegen * regen_multiplier
```

The greater this number is (from 1) the faster stamina will be regenerated.

### Usage Multiplier

**Configuration element name:** `usage_multiplier` \
**Type:** `float`&#x20;

The multiplier for the amount of Stamina that is used while sprinting.\
The formula is the same used for the [Regeneration Multiplier](stamina.md#regeneration-multiplier) but for the usage.

The greater this number is (from 1) the faster stamina will deplete.
