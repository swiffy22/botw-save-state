# Save State Code Documentation
**Version 1.1.1 (02/21/2022) - by Swiffy22**

After tons of effort, lots of patience, and the help of a dozen people along the way, I’m proud to present Breath of the Wild’s first major practice tool. This repository will serve as a place to store and update the codes and document any quirks that come along with using them.  Click on the listed feature to jump to the [known issues](#known-issues) for them. To be clear, this code does not at all create a “true” save state. Rather, it saves some of the most important values that you can restore later. Holding pause and dpad left will create the save state, holding pause and dpad right will restore it. You can press them in either order. Due to limitations with Atmosphere’s code handler, the code is split into four parts, which I’ve attempted to split in a sensical way.

## The Codes

The first code stores the most useful variables for practice. When you launch the game, there’s a roughly 25% chance that the Position reset function will not work. Simply close the game and launch it again. Once it’s working, it will continue working until you close the game again.

    [Save State: Position (Pause+Dpad L = Save, Pause+Dpad R = Restore)]

* [Link’s Position](#links-position)
* [Link’s Facing Angle](#links-facing-angle)
* [Camera Pan](#camera-pan)
* [Fall Damage Reset](#fall-damage-reset)
* Health Restoration
* Stamina Restoration
* [Round Bomb Cooldown Reset](#roundsquare-bomb-cooldown-reset)
* [Square Bomb Cooldown Reset](#roundsquare-bomb-cooldown-reset)
* [Stasis Cooldown Reset](#stasis-cooldown-reset)

The second code deals solely with durability and arrow count. The pause menu must be open to store and reload these values, and you must have the original weapons/arrow type equipped to restore them properly. Be sure to check the “Known Issues” section for this code, as it is somewhat particular with how it works.

    [Save State: Durability (Pause+Dpad L = Save, Pause+Dpad R = Restore)]
    
* [Equipped Weapon Durability](#equipped-weaponshieldbow-durabilityarrow-count)
* [Equipped Shield Durability](#equipped-weaponshieldbow-durabilityarrow-count)
* [Equipped Bow Durability](#equipped-weaponshieldbow-durabilityarrow-count)
* [Equipped Arrow Count](#equipped-weaponshieldbow-durabilityarrow-count)

The third code stores timers for time of day, blood moon, heat and cold damage timers, and all potion effects.

    [Save State: Time, Potions, Blood Moon, Heat/Cold (Pause+Dpad L = Save, Pause+Dpad R = Restore)]

* [Time of Day](#time-of-day)
* [Blood Moon Timer](#blood-moon-timer)
* Heat/Cold Damage Timer
* [Speed Up Potion Timer](#potion-timers)
* [Attack Up Potion Timer](#potion-timers)
* [Defense Up Potion Timer](#potion-timers)
* [Heat Resistance Potion Timer](#potion-timers)
* [Cold Resistance Potion Timer](#potion-timers)
* [Flame Resistance Potion Timer](#potion-timers)
* [Shock Resistance Potion Timer](#potion-timers)
* [Stealth Up Potion Timer](#potion-timers)

The fourth code deals with timers and remaining uses for the Champion Abilities and Master Sword.

    [Save State: Champion Abilities (Pause+Dpad L = Save, Pause+Dpad R = Restore)]

* Revali’s Gale Cooldown Timer
* Urbosa’s Fury Cooldown Timer
* Daruk’s Protection Cooldown Timer
* Mipha’s Grace Cooldown Timer
* [Master Sword Cooldown Timer](#master-sword-cooldown-timer)
* Revali’s Gale Remaining Uses
* Urbosa’s Grace Remaining Uses
* Daruk’s Protection Remaining Uses

## Adding the Codes

You must have a homebrewed Switch running Atmosphere. These codes can be used with either Edizon or Breeze (and likely any other cheat handlers in Atmosphere). The following is a short list of instructions for adding the code to your Switch, with a few annotations from myself.

1. Download the cheat file and ensure it's named `8E9978D50BDD20B4.txt` (might show up as `8E9978D50BDD20B4` in windows). The download file can be found in this repository.
2. Open FTPd on Switch and connect from PC. \[You can download FTPd from the Homebrew store if you do not currently have it installed. Alternatively you can connect your SD Card to your PC.]
3. Place `8E9978D50BDD20B4.txt` in the directory `/atmosphere/contents/01007EF00011E000/cheats/` (create the file path if it doesn't exist)
4. Open BOTW
5. Open Breeze > Cheats > "Load Cheats from atm" \[This is the most reliable way I’ve found to force the codes to load, but it should also be doable through Edizon.]
6. Use the dpad and "Toggle cheat" to ensure the cheat is enabled (and whatever other cheats you might want)

If you have other cheats for botw, you can simply download the cheat file from your Switch in the same directory, add these codes using Notepad++ or another text editor, then transfer it over to your Switch. I’ve run into issues editing the text file with Window’s pre-installed Notepad, so Notepad++ is recommended.

## Known Issues
#### Link's Position
* When opening Breath of the Wild, there’s a roughly 25% chance that the Position reset code will not function. Simply close the game, reopen it, and re-enable the code. Once it’s working, it will continue working until you close the game again.
* The game can sometimes softlock when restoring over far distances, particularly from one dense area to another. Try to avoid restoring far away from your saved position to mitigate this.
* Link’s position will not reset if he’s shield surfing, climbing, or riding a mount. However, it does work if you have the glider open while still having the shield on your feet.
* When saving near a ledge, Link will often not have a chance to “attach” to the ground upon resetting his position if you are travelling at high speeds with glider open, such as with a windbomb or btb. Close your glider to stop your momentum and the code will work properly.
* Link’s position will be slightly offset if you restore it while he’s ragdolling. Activate the code again if you want him to return to the exact position.
* After travelling away from your saved position with a BLSS, restoring your position while still holding the bomb will cause you to zip towards the location you just restored from. Drop the bomb before restoring to mitigate this issue.
* Restoring a grounded position while in water will cause you to clip through the ground. Either leave the water or activate the code twice to restore properly.

#### Link's Facing Angle
- Occasionally will not reset. Seems to be dependent on what animation you're currently in. Activate the code again to restore properly.

#### Camera Pan
- Occasionally will not reset if ZL is held or the camera is actively being turned while restoring. Activate the code again to restore properly.

#### Fall Damage Reset
- If your saved position is directly on the ground, the code will occasionally not have time to reset this value before you take fall damage. The easiest way to mitigate this is to jump, pause midjump, and create your save position while off the ground.

#### Round/Square Bomb Cooldown Reset
- This does not reset the state of your bombs. So, for example, if a square bomb is still spawned after you windbomb, you’ll need to explode it to start the cooldown. You can then use the code to reset the cooldown immediately.

#### Stasis Cooldown Reset
- This does not work if you have an object that is currently stasised. Unstasis the object, then activate the code to reset the cooldown immediately.

#### Equipped Weapon/Shield/Bow Durability/Arrow Count
- This code works by accessing an area in memory that is only active when the game is paused. If you make a save state while unpaused or in the quick menu, these values will not be stored. Make sure you’re paused while making a save to store these values properly.
- The durability of the weapons you want to store must be equipped in both the pause menu and the overworld. If you swap weapons in the menu, make sure you unpause and pause again before creating a save state in order to update the weapons being held in the overworld.
- Similar to the previous point, you must equip the weapon you want to restore in both the menu and overworld before restoring. If you try to restore durability while holding a different weapon, that weapon will now have the originally stored weapon's durability. The same applies to arrows. For example, if you create a save state with 200 normal arrows and 10 fire arrows, then equip fire arrows and restore, you’ll now have 200 fire arrows.
- Weapons in the overworld must be unequipped and re-equipped after restoring in order to update their values. For example, let’s say you store a traveler’s shield with a durability of 12 and it now has a durability of 3. You pause your game to restore it, and it now appears to be restored in the menu. You pause and jump, and now it has a durability of 2. You pause your game again and see that your shield is badly damaged again. This is because the code only updates the durability value in the menu and not in the overworld. To fix this, either use the quick menu to swap to another weapon and swap back, or use the pause menu to unequip, unpause, then pause again to re-equip the weapon. Arrows do not have this issue.

#### Time of Day
- Restoring Time of Day bugs the weather slightly. The weather will briefly roll back to its previous phase before returning to the current weather. For example, restoring a save state in a sunny area where it had been rainy in the previous 4 hour block may cause the sky to darken for several seconds.


#### Blood Moon Timer
- The way the blood moon timer functions is that it gradually counts up to 2520 over the course of seven in-game days. If it has a value of 2520 or greater at midnight, then it sets a flag so that a blood moon will occur the next night. Unfortunately, I’ve been unable to find where this flag is stored, which means there’s a risk of carrying this flag back to an unintended day if restoring after time passes midnight. Try to avoid this if you expect a blood moon to happen soon.

#### Potion Timers
- Restoring potion timers will only work if the potion is still currently active. If a potion has ended, restoring will do nothing. 
- The code cannot change potion types. For example, if you use a cold resist potion, store it, use a speed food potion, then try to restore to get your cold resist potion back, it will set your speed food potion to zero and then no potion will be active.

#### Master Sword Cooldown Timer
- If the timer has hit zero and the Master Sword has been recharged, restoring will do nothing.


### General things the code can’t do
- Restore enemies health/position. You can reset this naturally in-game by moving far enough away from them and restoring.
- Restore to different maps. Your restore position will always put you at the coordinates you saved at relative to whatever map you’re currently on.
- Resetting progression. You can’t “uncomplete” a quest, getting a korok, obtaining a memory, etc.
- Reset items in the menu. Items are stored in a dynamic way that would make resetting them difficult at this time.

### Future potential improvements
- Allow for multiple savestates (depending on feedback/community needs.)
- Save and restore camera tilt. (Tested this and ran into issues with the camera flipping upside down for a few frames after a restore. Will likely need more parts of the camera functions stored to work properly.)
- Save and restore skew. (I’ve found one section relating to skew that’s within the facing angle function. It might be possible to search for the skew value based on what’s shown here and find where it’s retained.)
- Improve weapon durability save and restore system. (I found where the overworld durability values are stored, but they’re in a very volatile area in memory. I couldn’t find a pointer that would reliably link to these values. Would like to look into this again later.)


## Credits
- BingsF - Huge help in talking me through some of the new things I’ve learned. Quickly understood the Atmosphere codetypes and helped with implementing them. Wrote the first successful teleport code.
- DarkFlareGaming - Made a teleport code for SMM2 which I modeled the early versions of this code around. Made very helpful videos about how to use Noexs and PointerSearch, which got me started with all of this in the first place. Also helped me directly in the early stages.
- Skoolzout1 - Made several codes for Botw on Wii U years ago. Has been super helpful with walking me through how to search for certain values and how the codes he made function.
- TheRealNoman - Offered to help me with this whole endeavor early on and encouraged me to continue on until we figured it out.
- iTNTPiston - Made an assembler which optimized the code and made it significantly shorter than it would have been otherwise. Also helped with code testing and helped with looking through decomp files to search for helpful functions.
- Tomvita - Helped me with understanding codetypes and some of the code handlers limitations.
- Snakes - Helped me with troubleshooting issues I was having with loading the code.
- Crazy_p - Informed me about the issue I was having with Notepad, which is why I couldn’t get my code to load.
- Jhmiller - Offered examples of the 0xA codetype, which is used heavily in the save state code, and explained his own code line by line.
- GamerJin - Linked me to a newer version of Noexs, as the one I was trying to use was outdated.
- Leoetlino - Head of the botw decomp project. The whole reason we had functions to explore in the first place.
- Savage13 - Offered some ideas for where to look for Link’s positional data.

## Changelog
- 1.0.0 (12/19/21) - Initial Release
- 1.0.1 (12/28/21) - Fixed a small issue where the bomb rune cooldown would not fully reset. Changed value from 90 to 181.
- 1.0.2 (01/16/22) - Fixed an issue where keybinds did not match description.
- 1.1.0 (01/28/22) - Added Heat and Cold Timer save and restore function. Further increased value for bomb rune cooldown. Changed value from 181 to 360.
- 1.1.1 (02/21/22) - Added an “if” statement to the durability code. The code will no longer store a value if the pause menu is not open (if the pointer is null), nor will it write to equipment values if the stored values are 0 (if the values stored in main memory are 0 or have not been written to.)
