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
- Use of flat reductions. However, this should be relegated to "secondary" damagetypes.
- Use of coefficient damage reductions (normal % resistances) to be strongly curtailed for damage types for which AC/AP systems are in use
   Just pierce/slash for now.
- Attacks whose AP is equal to or less than the target's AC are not considered to have "penetrated," and are instead transferred to a secondary damagetype and subject to its damage modifiers.
   In the case of pierce and slash (the only two which will be have this behavior for now) the secondary damagetype will be blunt damage.
   This secondary damagetype will be used for most flat reductions.
- Attacks whose AP exceeds the target's AC are considered to have "penetrated," and deal the listed damagetype.

# Code specifics and TODOs
- New DamageModifier called "ArmorClass." (done!)
- new damage property called "ArmorPiercing" if that doesn't exist already
- make them actually interact in, probably like damagespecifier or some similar shite
- Revalue ***EVERY PHYSICAL WEAPON*** to use AP unless they're defaults, probably have those at like 1 (holy shit)
- Revalue ***EVERY ARMOR*** to use AC and blunt damage reduction (holy shit x2)
- Actually make those balanced (will require 57,234 player-hours of live server testing)

# General balance niches/notes
