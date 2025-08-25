# Armor Rework design dock
# NavySerray
# Foreword
Combat in ss14 faces a number of balancing issues. This PR WILL NOT fix all of them.
In fact, it will most likely NEGATIVELY affect game balance until the system matures and balance is ironed out according to player feedback.
I am but one man and cannot fully forsee all the effects sweeping changes such as the ones this system is intended to enable.
However, despite this, i hope that this system, when implemented, will allow for the balance of the game to be improved greatly.

# Design goals
- Allow for more balancing options in general
- Allow for more variety in weapon and armor types generally
- Make armor feel more effective for both the attacker and victim
- Make guns (and more generally weapons) feel more effective for both the attacker and victim
- Make the use of armory gear more impactful than "sec have stronger gun"
- Make crew-sided guns more effective in intended roles (vent creatures etc) while curtailing their usefulness against prepared targets
- Make weapon/armor choice more dependant on intended use
- Finally stop people whinging about salv weapons being too good against crew without taking them out behind the shed
- Do something about incends being busted

# Broad strokes
- New property of armor - armor class, hereafter abbrieviated AC. Specific to damage type, e.g. "pierce AC, slash AC"
- New property of damage - armor piercing, hereafter abbreviated AP.
- Use of flat reductions ("padding"). However, this should be relegated to "secondary" damagetypes.
- Use of coefficient damage reductions (normal % resistances) to be strongly curtailed for damage types for which AC/AP systems are in use.
   - Just pierce/slash to be handled with AP for now.
- Attacks whose AP is equal to or less than the target's AC are not considered to have "penetrated," and are instead transferred to a secondary damagetype and subject to its damage modifiers.
   In the case of pierce and slash (the only two which will be have this behavior for now) the secondary damagetype will be blunt damage.
   This secondary damagetype will be used for most flat reductions.
- Attacks whose AP exceeds the target's AC are considered to have "penetrated," and deal the listed damagetype.
- MAYBE a system that increases flat damage reductions when a round has significantly less AP than the armor's AC?

# Code specifics and TODOs
- New DamageModifier called "ArmorClass." (done!)
- new damage property called "ArmorPiercing" if that doesn't exist already
- make them actually interact in, probably like damagespecifier or some similar shite
- Revalue ***EVERY PHYSICAL WEAPON*** to use AP unless they're defaults, probably have those at like 1 (holy shit)
- Revalue ***EVERY ARMOR*** to use AC and blunt damage reduction (holy shit x2)
- Actually make those balanced (will require 57,234 player-hours of live server testing)

# General balance niches/notes

## AP ammo
AP ammo should have increased ap at the cost of lower damage. It should be availible to sec as a tier 1 tech but be forbidden from use outside red alert.
It should still broadly be an increase to the cartridge's existing AP value. For example, AP pistol ammo should only be as good or worse than base rifle ammo.
Emagging protolathes should not allow production of AP ammo for balance reasons.

# Guns
Pistols
### General
The handy sidearm, carried when long guns would be inconvenient due to bulk or concealment. Not the best, but it's what you have - or can sneak around with.
- Lacking AP
- Bad recoil, making sprays highly inaccurate
- Highly concealable
- Cheap for traitors, widely issued for secoffs.
### Automatic Pistols
- High firerate greatly exacerbates poor recoil.
- Great burst damage at very close range.
### Revolvers
- Slightly higher AP, enough to punch through basic sec armor.
- Magnum rounds will do good damage even if they can't pierce armor due to their high single-shot damage
- Somewhat better accuracy
- Bad mag capacity and inconvenient reload handling
- Python comes with capable AP ammo, enough to punch through any crew armor.
### Cobra
- .25 caseless should have enough AP to go through basic sec armor vests and command suits, but not hos/cap or armory armor.

## SMGs
### General
Compact, easy to handle, and boasting big mags and the lowest recoil. Capable of quickly dispatching unarmored targets reliably with comparatively accurate automatic fire.
- Superior recoil control
- Superior capacity
- Decent accuracy
- Shares ammo with pistols - inherits their low AP.
### WT550
- This one is hard to handle if pistol caliber is going to be broadly less useful vs nukies/armored targets.
- Could add a new pistol caliber that's a rough 5.7x28mm analogue with slightly more rifle-like (higher AP, lower damage) stats? not sure if there'd be enough leeway 
### C20
- Lower firerate slightly, MASSIVELY increase controllability when wielded.
- Traitor c20 wielders will be balanced out by lack of AP.
- If the wt550 gets a new ammo type, give nukies a c20 variant that uses that round instead

-
## Shotguns
### General
The most versatile tools in your arsenal, capable of loading a wide variety of rounds from slugs to buckshot to flares.
- Performance completely determined by ammo type.
- Highly versatile, can be carried with multiple ammotypes.
### Buckshot
- Fires multiple low AP (worse than pistols) pellets.
- Poor performance against armor - worse than pistols - due to this.
- High damage vs unarmored threats.
- Increase pellet count, decrease per-pellet damage.
### Slugs
- The best option sec has aside from rifles vs armored threats.
- Middling AP, but doesn't need to penetrate - the blunt impact alone is enough to deal substantial damage.
- Not as accurate as a rifle.
- Could probably use slightly reduced base damage.
### Buck and Ball
- New proposed ammotype
- Multiple buckshot pellets surrounding a larger ball in the center closer to a slug.
- Provides versatile performance

## Assault Rifles / Carbines
### General
Military-grade rifles, designed for killing armored human targets. Large with mediocre handling.
- High base AP - enough to penetrate a bloodred suit.
- Lowered base damage to match.
- AP ammo for these is particularly expensive and deals even less damage. Serves one purpose - jugg hunting.

# Melee Weaponry
### General
Melee AP should generally reflect how "well-built" they are for the job.
ex. energy sword being able to penetrate basically everything, cap sword and ninja sword being good, a maints spear being reasonable, and a shiv being almost nothing.
Esword and edagger should be reliable armor-piercing options at the cost of range.

# Armor
## Sec armor
Armorvest - basic protection able to resist improvised weapons and sidearms. Ineffective vs a prepared attacker.
Riot suit - Excellent slash AC and high blunt damage reduction with pierce AC no higher than the armorvest.
Bulletproof vest - bread and butter vs active shooters, with high pierce AC and reasonable padding but slash AC no higher than armorvest.
Sec Hardsuit - Direct improvement of armorvest, featuring better padding and AC all-round.

## Head armor
Captain's armor - Best-in-slot AC for crew all-round and decent padding.
Head of security coats - AC not quite as good as captain's, but better padding.
CE/RD suits - armorvest level AC with worse padding.

## Improvised armor
Generally low padding and severe movement debuffs but actually quite good AC. Ned Kelly time.

## Syndie armor
Webvest - AC high enough to protect against non-armory weapons with excellent padding. Beware an armed sec.
Raidsuit - Good AC, high speed, high padding.
Bloodred - Good padding and good AC - enough to stop even AP pistol ammo.
Elite - Worse padding than the bloodred but with more speed and good laser resistance.
Juggsuit - Resists even rifle rounds and has excellent padding. Cybersun extends their glory to you - in your next shift: Robustness. (make it a bit costlier though)
