---
icon: wand-magic-sparkles
---

# Effects

**Effects** are an important game mechanic and you can, with UCR, give as many effects as you want to your Custom Roles.

**Note:** every effect will be added to the player as soon as they spawn as the Custom Role!

The **Effects** object should look like this:

```yaml
effects:
- effect_type: AntiScp207
  duration: -1
  intensity: 50
  removable: false
```

As you can see the `effects` config param is an array of Effect objects.

### Effect Type

**Configuration element name:** `effect_type` \
**Type:** [`EffectType`](../../c-notions/enums.md#effecttype)&#x20;

**This configuration value is an Enum**: please visit the [Enums](../../c-notions/enums.md) page in order to learn more about them!

The effect you want to give to the Custom Role.

### Duration

**Configuration element name:** `duration` \
**Type:** `float`&#x20;

The duration, in seconds, of the effect.\
If the duration is `-1` than the effect will last forever unless they remove it with SCP-500.

### Intensity

**Configuration element name:** `intensity` \
**Type:** `byte`&#x20;

The intensity of this effect.\
The value must be between `1` and `255`.

### Removable

**Configuration element name:** `removable` \
**Type:** `bool`&#x20;

Whether this effect can be removed by SCP-500.
