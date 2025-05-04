---
icon: rectangle-history
---

# Enums

**Enums** are a common type in almost every programming language because they have a special behavior: they can only can take only a finite set of predefined values.

**EXILED** does use enums when talking about roles, rooms, items, ammo and everything that is defined.

Here you'll find every EXILED enum in order to configure your role as best as possible.

## RoleTypeId and Team

<table><thead><tr><th width="48">Id</th><th>RoleTypeId</th><th>Team</th><th>Side</th><th>LeadingTeam</th></tr></thead><tbody><tr><td>-1</td><td>None</td><td>Dead</td><td>None</td><td>Draw</td></tr><tr><td>0</td><td>Scp173</td><td>SCPs</td><td>Scp</td><td>Anomalies</td></tr><tr><td>1</td><td>ClassD</td><td>ClassD</td><td>ChaosInsurgency</td><td>ChaosInsurgency</td></tr><tr><td>2</td><td>Spectator</td><td>Dead</td><td>None</td><td>Draw</td></tr><tr><td>3</td><td>Scp106</td><td>SCPs</td><td>Scp</td><td>Anomalies</td></tr><tr><td>4</td><td>NtfSpecialist</td><td>FoundationForces</td><td>Mtf</td><td>FacilityForces</td></tr><tr><td>5</td><td>Scp049</td><td>SCPs</td><td>Scp</td><td>Anomalies</td></tr><tr><td>6</td><td>Scientist</td><td>Scientists</td><td>Mtf</td><td>FacilityForces</td></tr><tr><td>7</td><td>Scp079</td><td>SCPs</td><td>Scp</td><td>Anomalies</td></tr><tr><td>8</td><td>ChaosConscript</td><td>ChaosInsurgency</td><td>ChaosInsurgency</td><td>ChaosInsurgency</td></tr><tr><td>9</td><td>Scp096</td><td>SCPs</td><td>Scp</td><td>Anomalies</td></tr><tr><td>10</td><td>Scp0492</td><td>SCPs</td><td>Scp</td><td>Anomalies</td></tr><tr><td>11</td><td>NtfSergeant</td><td>FoundationForces</td><td>Mtf</td><td>FacilityForces</td></tr><tr><td>12</td><td>NtfCaptain</td><td>FoundationForces</td><td>Mtf</td><td>FacilityForces</td></tr><tr><td>13</td><td>NtfPrivate</td><td>FoundationForces</td><td>Mtf</td><td>FacilityForces</td></tr><tr><td>14</td><td>Tutorial</td><td>OtherAlive</td><td>Tutorial</td><td>Draw</td></tr><tr><td>15</td><td>FacilityGuard</td><td>FoundationForces</td><td>Mtf</td><td>FacilityForces</td></tr><tr><td>16</td><td>Scp939</td><td>SCPs</td><td>Scp</td><td>Anomalies</td></tr><tr><td>17</td><td>CustomRole</td><td>Dead</td><td>None</td><td>Draw</td></tr><tr><td>18</td><td>ChaosRifleman</td><td>ChaosInsurgency</td><td>ChaosInsurgency</td><td>ChaosInsurgency</td></tr><tr><td>19</td><td>ChaosMarauder</td><td>ChaosInsurgency</td><td>ChaosInsurgency</td><td>ChaosInsurgency</td></tr><tr><td>20</td><td>ChaosRepressor</td><td>ChaosInsurgency</td><td>ChaosInsurgency</td><td>ChaosInsurgency</td></tr><tr><td>21</td><td>Overwatch</td><td>Dead</td><td>None</td><td>Draw</td></tr><tr><td>22</td><td>Filmmaker</td><td>Dead</td><td>None</td><td>Draw</td></tr><tr><td>23</td><td>Scp3114</td><td>SCPs</td><td>Scp</td><td>Anomalies</td></tr><tr><td>24</td><td>Flamingo</td><td>Flamingo</td><td>Flamingo</td><td>Flamingo</td></tr><tr><td>25</td><td>AlphaFlamingo</td><td>Flamingo</td><td>Flamingo</td><td>Flamingo</td></tr><tr><td>26</td><td>ZombieFlamingo</td><td>SCPs</td><td>Scp</td><td>Anomalies</td></tr></tbody></table>

## EffectType

```
AmnesiaItems
AmnesiaVision
Asphyxiated
Bleeding
Blinded
Burned
Concussed
Corroding
Deafened
Decontaminating
Disabled
Ensnared
Exhausted
Flashed
Hemorrhage
Invigorated
BodyshotReduction
Poisoned
Scp207
Invisible
SinkHole
DamageReduction
MovementBoost
RainbowTaste
SeveredHands
Stained
Vitality
Hypothermia
Scp1853
CardiacArrest
InsufficientLighting
SoundtrackMute
SpawnProtected
Traumatized
AntiScp207
Scanned
PocketCorroding
SilentWalk
Marshmallow (Obsolete)
Strangled
Ghostly
```

## ItemType

```
[0] KeycardJanitor 
[1] KeycardScientist 
[2] KeycardResearchCoordinator 
[3] KeycardZoneManager 
[4] KeycardGuard 
[5] KeycardMTFPrivate 
[6] KeycardContainmentEngineer 
[7] KeycardMTFOperative 
[8] KeycardMTFCaptain 
[9] KeycardFacilityManager 
[10] KeycardChaosInsurgency 
[11] KeycardO5 
[12] Radio 
[13] GunCOM15 
[14] Medkit 
[15] Flashlight 
[16] MicroHID 
[17] SCP500 
[18] SCP207 
[19] Ammo12gauge 
[20] GunE11SR 
[21] GunCrossvec 
[22] Ammo556x45 
[23] GunFSP9 
[24] GunLogicer 
[25] GrenadeHE 
[26] GrenadeFlash 
[27] Ammo44cal 
[28] Ammo762x39 
[29] Ammo9x19 
[30] GunCOM18 
[31] SCP018 
[32] SCP268 
[33] Adrenaline 
[34] Painkillers 
[35] Coin 
[36] ArmorLight 
[37] ArmorCombat 
[38] ArmorHeavy 
[39] GunRevolver 
[40] GunAK 
[41] GunShotgun 
[42] SCP330 
[43] SCP2176 
[44] SCP244a 
[45] SCP244b 
[46] SCP1853 
[47] ParticleDisruptor 
[48] GunCom45 
[49] SCP1576 
[50] Jailbird 
[51] AntiSCP207 
[52] GunFRMG0 
[53] GunA7 
[54] Lantern 
[55] Snowball
[56] Coal
[57] SpecialCoal
[58] Tape
```

## ItemCategory

```
Keycard
Medical
Radio
Firearm
Grenade
SCPItem
SpecialWeapon
Ammo
Armor
```

## AmmoType

```
Nato9
Nato556
Nato762
Ammo12Gauge
Ammo44Cal
```

## SpawnType

```
CompleteRandomSpawn
ZoneSpawn
RoomsSpawn
SpawnPointSpawn
KeepRoleSpawn
KeepCurrentPositionSpawn
ClassDCell
RoleSpawn
```

## ZoneType

```
LightContainment 
HeavyContainment 
Entrance         
Surface      
```

## RoomType

```
LczArmory
LczCurve
LczStraight
Lcz330
Lcz914
LczCrossing
LczTCross
LczCafe
LczPlants
LczToilets
LczAirlock
Lcz173
LczClassDSpawn
LczCheckpointB
LczGlassBox
LczCheckpointA
Hcz079
HczEzCheckpointA
HczEzCheckpointB
HczArmory
Hcz939
HczHid
Hcz049
HczChkpA
HczCrossing
Hcz106
HczNuke
HczTesla
HczTestRoom
HczElevatorA
HczElevatorB
HczServers
HczChkpB
HczTCross
HczCurve
Hcz096
EzVent
EzIntercom
EzGateA
EzDownstairsPcs
EzCurve
EzPcs
EzCrossing
EzCollapsedTunnel
EzConference
EzStraight
EzCafeteria
EzUpstairsPcs
EzGateB
EzShelter
Pocket
Surface
EzCheckpointHallway
HczTestRoom
```
