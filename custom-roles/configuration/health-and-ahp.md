---
icon: heart-pulse
---

# Health and AHP

Having custom **Healt** (HP) and **Artificial Health** (AHP) is an important way to customize even more your Custom Roles.\
With our powerful product you can decide almost everything about these two behavior.

## Health

The **Health** object should look like this:

```yaml
health:
  amount: 100
  maximum: 100
```

### Amount

**Configuration element name:** `amount` \
**Type:** `int32`&#x20;

The amount of HP that will be given to the player when they first spawn as this Custom Role.\
If the amount is bigger than the maximum then the maximum will be equal to the amount.

### Maximum

**Configuration element name:** `maximum` \
**Type:** `int32`&#x20;

The maximum amount of HP that a player can have (and regenerate)

***

## Artificial Health (AHP)

The **AHP** object should look like this:

```yaml
ahp:
  amount: 0
  limit: 75
  decay: 1.20000005
  efficacy: 0.699999988
  sustain: 0
  persistant: false
```

### Amount

**Configuration element name:** `amount` \
**Type:** `int32`&#x20;

The amount of AHP given to the player when they first spawn as this Custom Role.\
\
**Note:** due to a game limitation, the maximum number of AHP that will be displayed to the player is **75** but this doesn't mean that if you assign 300AHP the player won't have them: the 225 will be just hidden.

### Limit

**Configuration element name:** `limit` \
**Type:** `int32`&#x20;

The player's AHP limit when they are this Custom Role.\
They won't be able to gain more AHP (like with Adrenaline) than this limit.

### Decay

**Configuration element name:** `decay` \
**Type:** `float`&#x20;

The decay speed of the AHP in AHP/s (so if you put `decay: 2` the player will lose 2AHP every second)

### Efficacy

**Configuration element name:** `efficacy` \
**Type:** `float`&#x20;

The efficacy (in percentage where 0% is 0 and 100% is 1) of the AHP.\
This indicates how much damage does the AHP take instead of the player: for example, if the `efficacy: 0.9` (really high) and a player deal a `50HP` damage to this Custom Role he would receive only `5HP` damage directly and the other `45HP` will be absorbed by the AHP.

### Sustain

**Configuration element name:** `sustain` \
**Type:** `float`&#x20;

The time (in seconds) where the AHP won't decay.\
They'll start decaying as soon as this time ends.

### Persistant

**Configuration element name:** `persistant` \
**Type:** `bool`&#x20;

Whether the AHP can decay or not.
