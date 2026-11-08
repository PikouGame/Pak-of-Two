# Pak of Two (PoT)

*A bond strong enough to call two companions to your side.*

A craftable accessory that allows **two active party Pals**
while equipped in one of the game's accessory slots. This changes the active
companion limit, not the number of Pals carried in the party.

**Research stage. No installable mod has been built.**

## Intended behavior

- Craft the accessory and equip it in a normal accessory slot.
- Allow one additional owned party Pal while the accessory is equipped.
- Enforce eligibility and the two-Pal limit on the server.
- Multiple copies should not increase the limit beyond two.
- Unequipping removes the extra companion through normal recall behavior.
  Mounting, death, teleportation and disconnects need explicit lifecycle tests.

The working implementation assumption is a client-and-server mod: clients
need the custom item's name, icon and recipe; the server owns summon checks.
The crafting cost, unlock level, controls and partner-skill interactions are
not settled yet.

## Evidence and next step

The [public SDK](https://github.com/localcc/PalworldModdingKit/tree/e6632458b97af0083eb81715775651b08104ef6a)
declares four accessory slot identifiers, inventory equipment lookup methods,
and companion activation/recall methods. These declarations identify places
to investigate; they do not prove that a second ordinary companion works in
the installed game. A class containing `FirstOtomoPal` and `SecondOtomoPal`
also exists, but its actual gameplay use has not been established.

Next: inspect the live companion holder and equipment data, then test a second
existing party Pal without duplicating its saved identity. Once that lifecycle
works, implement the custom accessory, recipe and equipment gate.

Not verified: simultaneous companion AI, multiplayer replication, custom item
registration, crafting, equip/unequip cleanup, partner skills and save integrity.
