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

The journal overlay (bottom-right of the 3D view) shows the current quest or **Money making**, the step, and Pause / Skip / Stop.

- **Current** — what it is doing now
- **Queue** — remaining quests in prerequisite order
- **Blocked** — missing skills, QP, or prerequisite quests
- **Session** — runtime / completions

If nothing left in the queue can run because of skills, the **centre-of-screen** banner stays up until you press Stop.

## Scripts in this repo

One `.js` file per quest (63 files). Load the file for the quest you want; the shared engine still does money making, gathering, and requirement checks first. The file list on GitHub is the full set.

Shield of Arrav and Hero's Quest need a **partner** on the other gang for the certificate / master thief armband unless you already have one banked. Set the partner name in the script settings before you start.
