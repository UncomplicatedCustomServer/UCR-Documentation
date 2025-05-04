---
icon: shield-halved
---

# Hume Shield

The **Hume Shield** is a key mechanic for SCPs and because of that it's really important to learn how to customize it.\
UCR does actually includes pretty powerful tools for doing that.

The **Hume Shield** object should look like this:

```yaml
hume_shield:
  amount: 0
  maximum: 0
  regeneration_amount: 2
  regeneration_delay: 7.5
```

### Amount

**Configuration element name:** `amount` \
**Type:** `int32`&#x20;

The amount of Hume Shield given to the player when they first spawn as this Custom Role.

### Maximum

**Configuration element name:** `maximum` \
**Type:** `int32`&#x20;

The maximum amount of Hume Shield that the player as this Custom Role can have.

The amount can be lower than the maximum as the role can gain Hume Shield from the regeneration!

### Regeneration Amount

**Configuration element name:** `regeneration_amount` \
**Type:** `float`&#x20;

The amount of Hume Shield that should be given to the player every second (it's in HS/s).\
`0` will disable the generation.

### Regeneration Delay

**Configuration element name:** `regeneration_delay` \
**Type:** `float`&#x20;

The delay, in seconds, from the last damage dealt to the SCP from where they'll start to regenerate Hume Shield again following the [Regeneration Amount](hume-shield.md#regeneration-amount).
