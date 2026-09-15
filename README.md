<p align="center"><u><b>ANY PROBLEMS/QUESTIONS ADD .benzyme ON DISCORD</b></u></p>
<p align="center"><u><b>I'M A LOVELY GUY AND WOULD LOVE TO ANSWER YOUR QUESTIONS</b></u></p>

<p align="center">
  <a href="https://rs2b2t.com/discord" rel="noopener noreferrer" target="_blank">
    <img width="600" alt="rs2b2t-discord-banner" src="https://i.imgur.com/tAEkgGQ.png" />
  </a>
</p>

<p align="center">Quest scripts for <a href="https://rs2b2t.com/">https://rs2b2t.com/</a> (Lost City revision 289).</p>

<p align="center"><u><b>THESE SCRIPTS CAN BE USED FOR WHATEVER YOU LIKE REGARDING YOUR OWN SCRIPTS/PERSONAL USE JUST PLEASE GIVE ME CREDIT.. IF YOU FEEL LIKE IT</b></u></p>

1. Load the bot client via url: https://w1.rs2b2t.com/rs2b0t/ (Make an account via https://rs2b2t.com/register if you haven't already)
2. Log into your account
3. Click browse up the top right of the client
4. Download a script from this repo and locate/run it off your PC

Most scripts dismiss the welcome screen on start and skip Tutorial Island if you are still there.

## Status — fixing every quest one by one

Every 2004 / Lost City quest that has a script in this folder is **in the queue to be fixed properly, one at a time**. The files here are the current engine: they already walk, buy, gather, and talk, but a given quest may still get stuck, take a bad door, or mishandle an item until that quest has had its pass.

When a quest has been through that pass it should:

- finish from a fresh account that meets the real skill / quest / QP gates
- gather or buy everything it needs (ironman-style, see below)
- path on the 289 map without teleports
- recover from death, randoms, and closed doors

Until then, treat anything that is not Cook's Assistant-level simple as **work in progress**. If one breaks, skip it or ping me on Discord and I will put it next in the fix list.

Want every implemented quest in one run instead of a single file? Use **AIOQuester** from [RS2B2TScripts](https://github.com/Benzymee/RS2B2TScripts). Same engine, same rules; the queue still runs prerequisites first.

## What happens before any quest starts

### Money making (5,000 gp)

No quest starts until the character has **5,000 gp** in inventory plus bank. The HUD labels this **Money making**.

The script boats or walks to East Ardougne (never White Wolf Mountain, never the wilderness lever), then:

1. Pickpockets the Ardougne **man** in the house around `2624, 3295` until Thieving 5 (opens the door if he is inside)
2. Steals **cakes** from the baker stall to a stock of 100 (kites a catching **guard** out of the square — this is the only time guards are kited)
3. Pickpockets the best NPC your Thieving allows: Man → Warrior woman (25) → Guard (40) → Knight (55) → Paladin (70) → Hero (80)

A failed pickpocket is only a stun. Wait it out and continue. Do not expect a kite unless a stall guard actually attacks you.

If you are broke on the Asgarnia side of the mountain, it pickpockets local men for the **60 gp** ship fare first, then takes Port Sarim → Karamja → Brimhaven → Ardougne (the same boat chain as `SneakyArdougne.js`).

### Prerequisites, skills, and quest points

The engine will not start a quest the account cannot legally do.

| Gate | What it checks | If you do not have it |
|---|---|---|
| **Prerequisite quests** | Earlier quests that this one requires (e.g. Merlin's Crystal before Holy Grail, Jungle Potion before Shilo Village) | The quest is **BLOCKED**. The queue skips it and runs anything else that is ready. Finish the missing quest (or tick it in AIOQuester) and it unblocks. |
| **Skill levels** | The quest's real skill reqs, including levels needed to gather items the ironman way (mine, smelt, cook, craft) | The quest is **BLOCKED**. A red banner is painted in the **centre of the game screen** naming the quest and lines like `Needs Mining 15 (have 7)`. The script **idles on that banner** until you Stop — it does not grind the skill for you. |
| **Quest points** | Listed QP requirements | Same as skills: **BLOCKED**, shown on the journal / Blocked tab. No centre banner (that banner is skills only). |
| **Items** | Listed start items | The engine **buys or gathers** them. A missing item is not a hard stop once the quest is in progress; mid-quest the module sources whatever it still needs. |

Tick order in AIOQuester does not matter. The built-in queue always puts **prerequisites first**. A standalone file in this repo still uses that engine: if you load Holy Grail without Merlin's Crystal, it will sit blocked rather than force the quest.

**Quests I can do** (AIOQuester live picker) selects only quests this character's stats, QP, and completed quests allow. Items are fetched by the script, so they do not hide a quest you could otherwise start.

## Ironman gathering (shops still count)

Scripts gather like an ironman:

- **NPC shops that actually stock the item** (count &gt; 0) are valid. Buy from them as a normal account would.
- If the shop row is empty / baseline 0, the script **mines, smelts, fishes, cooks, or crafts** instead of assuming the bank already has it.
- Skill requirements for those gather methods are part of the quest gate. If you cannot smelt the iron bar The Knight's Sword needs, you get the centre-screen skill banner, not a freeze at the furnace.

## Pathing

- Walks **on foot**. Teleports are off.
- Routes use the **Lost City 289** map (doors, ships, dungeons as they exist on RS2B2T).
- **White Wolf Mountain is never the route.** Crossing Asgarnia ↔ Kandarin is the Port Sarim / Karamja / Brimhaven / Ardougne boat chain.
- The Ardougne **wilderness lever** is not used to skip that trip while making money or travelling for quests.

## HUD

The journal overlay (bottom-right of the 3D view) shows the current quest or **Money making**, the step, and Pause / Skip / **Requirements** / Stop.

- **Current** — what it is doing now
- **Queue** — remaining quests in prerequisite order
- **Blocked** — missing skills, QP, or prerequisite quests
- **Session** — runtime / completions
- **Requirements** — skill, QP, and prerequisite quest gates for the quests in this run (click the **Requirements** button to jump here)

If nothing left in the queue can run because of skills, the **centre-of-screen** banner stays up until you press Stop.

## Quest requirements

Lost City revision 289 gates used by these scripts. Skill levels include ironman gather methods the engine treats as start gates. Items are gathered or bought; they do not block a quest the way skills and prerequisite quests do.

| Quest | QP reward | QP required | Skills | Prerequisite quests | Items the script gathers |
|---|---:|---|---|---|---|
| Big Chompy Bird Hunting | 2 | — | Fletching 5, Cooking 30, Ranged 30 | — | — |
| Biohazard | 3 | — | — | Plague City | — |
| Black Knight's Fortress | 3 | 12 QP | — | — | Iron chainbody x1, Bronze med helm x1, Cabbage x1 |
| Clock Tower | 1 | — | — | — | — |
| Cook's Assistant | 1 | — | — | — | Egg x1, Pot of flour x1, Bucket of milk x1 |
| Death Plateau | 1 | — | Mining 15, Smithing 15, Fishing 20, Cooking 15 | — | — |
| Demon Slayer | 3 | — | — | — | — |
| Digsite Quest | 2 | — | Agility 10, Herblore 10, Thieving 25 | — | — |
| Doric's Quest | 1 | — | Mining 15 | — | Clay x6, Copper ore x4, Iron ore x2 |
| Dragon Slayer | 2 | 32 QP | Mining 30, Smithing 34, Crafting 8 | — | Coins x1, Lobster pot x1, Hammer x1, Wizard's mind bomb x1, Unfired bowl x1, Silk x1, Plank x3 |
| Druidic Ritual | 4 | — | — | — | Raw bear meat x1, Raw beef x1, Raw chicken x1, Raw rat meat x1 |
| Dwarf Cannon | 1 | — | — | — | — |
| Eadgar's Ruse | 1 | — | Herblore 31 | Druidic Ritual, Troll Stronghold | Raw chicken x5, Grain x10 |
| Elemental Workshop | 1 | — | Mining 30, Smithing 20, Crafting 20 | — | Leather x1, Needle x1, Thread x1, Coal x4, Knife x1, Hammer x1 |
| Ernest the Chicken | 4 | — | — | — | Oil can x1, Pressure gauge x1, Rubber tube x1 |
| Family Crest | 1 | — | Mining 40, Crafting 40, Smithing 40, Magic 59, Fishing 50, Cooking 45 | — | Tuna x1, Bass x1, Salmon x1, Shrimps x1, Swordfish x1, Ruby x2, Ring mould x1, Necklace mould x1, Death rune x4 |
| Fight Arena | 2 | — | — | — | — |
| Fishing Contest | 1 | — | Fishing 10 | — | — |
| Gertrude's Cat | 1 | — | — | — | — |
| Goblin Diplomacy | 5 | — | — | — | Goblin mail x3, Orange dye x1, Blue dye x1 |
| Hazeel Cult | 1 | — | — | — | — |
| Hero's Quest | 1 | 55 QP | Mining 50, Herblore 25, Fishing 53, Cooking 53 | Lost City, Dragon Slayer, Merlin's Crystal, Shield of Arrav | — |
| Holy Grail | 2 | — | Attack 20 | Merlin's Crystal | Excalibur x1 |
| Horror from the Deep | 2 | — | Agility 35, Smithing 34 | — | Plank x2, Nails x8, Hammer x1, Swamp tar x1, Molten glass x1 |
| Imp Catcher | 1 | — | — | — | Black bead x1, Red bead x1, White bead x1, Yellow bead x1 |
| Jungle Potion | 1 | — | Herblore 3 | Druidic Ritual | — |
| Legends Quest | 4 | 107 QP | Magic 56, Mining 52, Agility 50, Crafting 50, Smithing 50, Strength 50, Thieving 50, Woodcutting 50, Herblore 45, Prayer 42 | Hero's Quest, Family Crest, Shilo Village, Underground Pass, Waterfall Quest | Rune axe x1, Lockpick x1, Unpowered orb x1, Cosmic rune x3, Opal x1, Jade x1, Red topaz x1, Sapphire x1, Emerald x1, Ruby x1, Diamond x1, Gold bar x2, Papyrus x6, Charcoal x6 |
| Lost City | 3 | — | Crafting 31, Woodcutting 36 | — | — |
| Merlin's Crystal | 6 | — | — | — | Bread x1, Insect repellent x1, Bucket x1, Tinderbox x1 |
| Monk's Friend | 1 | — | — | — | — |
| Murder Mystery | 3 | — | — | — | — |
| Nature Spirit | 2 | — | Crafting 18, Mining 20, Smithing 20 | The Restless Ghost, Priest in Peril | — |
| Observatory Quest | 2 | — | Crafting 10 | — | — |
| Pirate's Treasure | 2 | — | — | — | Karamjan rum x1, White apron x1, Spade x1 |
| Plague City | 1 | — | — | — | — |
| Priest in Peril | 1 | — | — | — | Bucket x1 |
| Prince Ali Rescue | 3 | — | — | — | Coins x400, Bronze bar x1, Pink skirt x1, Redberries x1, Pot of flour x1, Tinderbox x1, Shears x1, Rope x2, Beer x3 |
| Regicide | 3 | — | Agility 56, Crafting 10 | Underground Pass | — |
| Romeo & Juliet | 5 | — | — | — | Cadava berries x1 |
| Rune Mysteries Quest | 1 | — | — | — | — |
| Scorpion Catcher | 1 | — | Prayer 31 | — | — |
| Sea Slug Quest | 1 | — | Firemaking 30 | — | — |
| Shades of Mortton | 3 | — | Crafting 20, Herblore 15, Firemaking 5 | Priest in Peril | — |
| Sheep Herder | 4 | — | — | — | — |
| Sheep Shearer | 1 | — | — | — | Ball of wool x20 |
| Shield of Arrav | 1 | — | — | — | — |
| Shilo Village | 2 | — | Crafting 20, Agility 32, Smithing 4, Mining 4, Prayer 10 | Jungle Potion | — |
| Tai Bwo Wannai Trio | 2 | — | Cooking 30, Agility 15, Fishing 5, Firemaking 30 | Jungle Potion | — |
| Temple of Ikov | 1 | — | Thieving 42, Ranged 40, Woodcutting 60, Fletching 65, Crafting 10 | — | — |
| The Fremennik Trials | 3 | — | Woodcutting 40, Crafting 40, Fletching 25 | — | Bronze axe x1, Knife x1, Tinderbox x1, Raw shark x1 |
| The Grand Tree | 5 | — | Agility 25 | — | — |
| The Knight's Sword | 1 | — | Mining 15, Smithing 15, Cooking 10 | — | Redberry pie x1, Iron bar x2 |
| The Restless Ghost | 1 | — | — | — | — |
| The Tourist Trap | 2 | — | Fletching 10, Smithing 20 | — | — |
| Tree Gnome Village | 2 | — | — | — | — |
| Tribal Totem | 1 | — | Thieving 21 | — | — |
| Troll Stronghold | 1 | — | Agility 15 | Death Plateau | — |
| Underground Pass | 5 | — | Thieving 50, Ranged 25 | Biohazard | Rope x1 |
| Vampire Slayer | 3 | — | — | — | Hammer x1, Garlic x1, Stake x1 |
| Watch Tower | 4 | — | Magic 14, Mining 40, Smithing 40, Herblore 14, Thieving 15, Agility 25 | — | Dragon bones x1, Guam leaf x1, Bat bones x1, Gold bar x1 |
| Waterfall Quest | 1 | — | — | — | Rope x1 |
| Witch's House | 4 | — | — | — | Cheese x1, Leather gloves x1 |
| Witch's Potion | 1 | — | — | — | Onion x1, Rat's tail x1, Burnt meat x1, Eye of newt x1 |

## Scripts in this repo

One `.js` file per quest (63 files). Load the file for the quest you want; the shared engine still does money making, gathering, and requirement checks first. The file list on GitHub is the full set.

Shield of Arrav and Hero's Quest need a **partner** on the other gang for the certificate / master thief armband unless you already have one banked. Set the partner name in the script settings before you start.
