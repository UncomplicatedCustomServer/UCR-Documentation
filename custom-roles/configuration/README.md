---
icon: person
---

# Configuration

The configuration of a UCR Custom Role is a simple YAML file where you can manage almost every aspect of the role.

The following file configuration is the current default one that the plugin generates.

```yaml
id: 1
name: 'Janitor'
override_role_name: false
nickname: 'D-%dnumber%'
custom_info: 'Janitor'
badge_name: 'Janitor'
badge_color: 'pumpkin'
role: ClassD
team: 
role_appearance: ClassD
is_friend_of: []
health:
  amount: 100
  maximum: 100
ahp:
  amount: 0
  limit: 75
  decay: 1.20000005
  efficacy: 0.699999988
  sustain: 0
  persistant: false
hume_shield:
  amount: 0
  maximum: 0
  regeneration_amount: 2
  regeneration_delay: 7.5
effects: []
stamina:
  regen_multiplier: 1
  usage_multiplier: 1
  infinite: false
max_scp330_candies: 2
can_escape: true
role_after_escape:
  default: InternalRole Spectator
  cuffed by InternalTeam ChaosInsurgency: InternalRole ClassD
scale:
  x: 1
  y: 1
  z: 1
spawn_broadcast: |-
  You are a <color=orange><b>Janitor</b></color>!
  Clean the Light Containment Zone!
spawn_broadcast_duration: 5
spawn_hint: 'This hint will be shown when you will spawn as a Janitor!'
spawn_hint_duration: 5
custom_inventory_limits: {}
inventory:
- Flashlight
- KeycardJanitor
custom_items_inventory: []
ammo:
  Nato9: 10
damage_multiplier: 1
spawn_settings:
  can_replace_roles:
  - ClassD
  max_players: 10
  min_players: 1
  spawn_chance: 60
  spawn: RoomsSpawn
  spawn_zones: []
  spawn_rooms:
  - LczClassDSpawn
  spawn_roles:
  - ClassD
  spawn_points: []
  required_permission: ''
custom_flags: 
ignore_spawn_system: false

```

In the following document we'll take a look at the main configuration elements and explain them, in order to allow you the best and easiest experience.

