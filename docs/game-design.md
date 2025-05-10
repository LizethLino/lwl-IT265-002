## Change Log

Made a grid based on in game grid code. Changed it so that it was based on player input and detects mouse clicks. Tiles you can click are determined by your neighboring tiles and have a highlight that indicates what they are.

Created character card prefab. Added a button to Hide and show the info of the card with the eventual expectation that I would use it during combat.

Made UI panel for combat and gameManager that handles speedBuff but not utilized for current build.

Added the event card sequences. Also added functionality to manually end turn after event card so we could see the team display before end turn. 

Automatic end turn added when normal tile movement.

Physical prototype had manual dice throws and selection of character cards and lead. The digital prototype automatically chooses the team leader as the character with the highest DEF. Same goes for combat sequences where it selects out of the alive characters and picks the character with the highest ATK.

Added a collapsable UI element that displays Debug.Log to show the prints to console as the game plays. Added this after I realized that the debug.Log technically isn't a part of the meaning the webGL deployment was very bare without it.

In combat for the physical prototype, combat would go until someone retreated or the whole team was dead. For digital prototype, combat is handled by system so you only have to wait for sequence to end. Also (not sure if this was for my random Enemy code) combat only goes until team lead dies and gets replaced.

---

## Game Title: System Failure
## Game Genre: Strategy RPG
Game Demo WebGL Link: https://lizethlino.github.io/lwl-IT265-002/SystemFailureGame/Ver3/

Video Demo Link: https://www.youtube.com/watch?v=W92Aafsofy0

## Summary

"Our world is bound by fate. Every action you have ever done or will one day do has already been determined. And yet, your world had the gall to liberate itself from universal laws. For your people's audacity, the world has been doomed to fall, but fear not! The last survivors will be allowed to escape with their lives. Be you good or bad, all are free to walk out on their own two feet. A game of survival where friends and foes my turn on one another, who will be the one to make it out alive with their sanity intact?"

The world is collapsing and any who come too close to the instability lose their minds to the corruption. A single portal remains open and it is your job to find you way to the portal with a method of opening the gate that seperates you from freedom. Dungeons have appeared in the farthest corners of the world that are home to weapons and tools. Traverse this ever growing dungeon filled with the shadows of your friends and family to find what you need. Outside of the dungeon you have some rooms that will provide you with other services but beware of the other teams that are trying for the same goal as you. If they see you as a threat, they may just choose to kill you or die trying.

---

## Why It Matters

The multiverse theory influences the concept of location tiles being color coded and giving certain characters higher speed. That way you know that certain characters are from post-apocalyptic worlds, cyberpunk cities, science motivated societies, etc.

---

## Objective
- Find the key first and make it to the gate alive or be the last team standing.

---

## Core Features Currently/To-Be Implemented
- __Unique Grid Generation:__ A new grid is generated at start of game.
- __Player Tile Movement:__ A player traverses a grid. The grid represents the world as it rips apart at the seams. Even as it breaks it attempts to stitch itself together leading to different worlds being forcibly combined into one leading to the broken world that is out grid.
- __Tile types:__ The tile type determines what world a certain patch belongs to. Characters have been brought from their own dimensions into this new patchwork world. This is how we get the phenomenon of HomeTurfAdvantage. If a character card on your team belongs to the same tile type (character card King is from the Kingdom, when on green tile...) they attain a speed buff that gives them an advantage during combat.
- __"HomeTurfAdvantage":__ Speed Buff (Not currently Implemented)
- __Player team cards:__ Each character gets a team of three unique characters. The character with the largest DEF will be your lead and take hits. The character with the largest ATK will deal hits to enemies.
- Character card special ability (Not currently Implemented)
- __Encounter random enemy combat:__ Chance encounter with a wandering corrupted character. (In the future add function to calculate HP based on CRRPT: newHP = currHP + (5*CRRPT))
- PvP combat  (Not currently Implemented)
- __Pull item add to inventory:__ Will pull an item from the item deck and add it to the inventory. Eventually you will be able to display your inventory and use an item.
- __Use item/displayed inventory:__ (Not currently implemented)
- __Event card effects with accept/reject function:__ You can accept the consequence or reject and increase corruption level by 1. If corruption level reaches 3, HP is automatically set to 0. In future builds this will be changed to initiate combat.

---

## Relevant Info

| **Character Type** | **Defined Stat** |
|--------------------|------------------|
|      **TANK**      |      MAX DEF     |
|     **SUPPORT**    |      MAX SPD     |
|     **DAMAGE**     |      MAX ATK     |

---

| **Tile Type** | **Color** |
|----------- ---|-----------|
|  **KINGDOM**  |   Green   |
|   **RUINS**   |   Orange  |
|    **LAB**    |    Grey   |
|   **MEDIA**   |    Pink   |
|    **CITY**   |    Blue   |
|  **FACTORY**  |    Red    |

## Character Card Display
![card example](https://github.com/user-attachments/assets/4a13a41b-c5c3-4654-bc1e-c9c0aa76791b)
Every character card display has am image on the left side.
The character info is shown on the left.
- Tile type is determined by color. In this example, the Derelict is from the CIITY.
- Character type is written in the colored box. In this example, the Derelict is a TANK and has the max DEF 2.
- Stats HP, ATK, DEF, SPD, CRRPT listed in second box.
- Special ability and its number of uses left is written on the bottom of the info.

## Consequence Card Display
![consequence event example](https://github.com/user-attachments/assets/3a227d29-41c9-4896-82ac-3ff60e34d0cc)
Consequence cards will command you to apply a consequence to your team. If you choose to ignore this, your character accumulates corruption.
- Effect to be applied if Accepted is written on top half.
- Alternative effect is shown in the bottom half if Rejected.

## Current UI Summary
- Start Game UI
  - Basic introductory title card with "Start Game" Button
- Turn UI
  - Left has the Debug.Log which shows the actions that just occured. Can be hidden using the bottom right corner button "Hide Log"
  - Show current player team by pressing "Show Team" button
  - If event card pulled, manually end turn with "End Turn" button
- PassDevice UI
  - Basic Pass device to specified player with "Continue" button
- Win UI
  - Has "Play Again" button

---

### Game Rules

On game begin, pick three cards from the character deck and select the one with the highest DEF to be your team leader. This will be the character that takes the damage during combat.
Once both players have their three cards, place your piece in the starting location and begin your turn. You can decide who goes first. A traditional rock paper scissors will suffice.

__On turn begin:__
1. move to one of the tiles connected to the starting tile. (Imagine that the starting tile in the final demo will be a long strip on the left side of the grid. Player can choose to jump onto any of the tiles next to the starting strip). Same logic applies to all consecutive turns. You are able to go onto any tile that neighbors your current one.
2. Depending on the tile color, your characters may get a speed buff due to HomeTurfAdvantage. All this means is that if the character card and tile type are the same, increase character speed by 1. This is relevent during combat. When not on matching tile, speed remains the same.
3. If the tile you land on has an opposing player, combat is initiated (read combat portion). If all character cards are dead, you automatically lose. You may choose to retreat to avoid/escape combat and jump within a certain radius of your current tile.
4. Every two turns pull a card from the event deck. The event deck has three types of unique events. The find item event, the encounter enemy event, and the special consequence event. The special event consequence card will grant you some sort of disadvantage. But fear not! You have two options when pulling an event card. Either accept and bear the weight of the consequence, or ignore and increment the corruption value of one of your character cards.
  - When corruption for any character reaches 3, they are now an enemy and combat will begin. Your remaining cards will fight against the corrupted character. (Read combat portion)
  - Before corruption reaches 3, your characters will find themselves becoming stronger. For every increase in corruption, HP increases by 5 pts. But once they reach corruption level 3, this increase in strength will make them a deadly foe. (crrpt = 0 -> hp = 20, crrpt = 1 -> hp = 25, ...). In this situation you may choose to abandon your teammate. Put them on the top of the character card deck and set their CRRPT = 3. They will be the next encountered enemy for whoever player pulls the card.
  - As for find item and encounter enemy events, these two have no consequences and cannot be ignored. The items you find each serve some sort of purpose and depending on what they are they can be used during combat or on the field grid (combat -> sword, field -> movement x2, ...). Encounter an enemy will initiate combat with your character cards and the encountered enemy (Read combat portion).
4. As you traverse the tiles, for every item card you pull you have a chance of finding a key. Once you have the key, race to the gate (like starting strip but on the right side) and get to the gate to win. Only those with keys can open the gate.
  - An opposing player may choose to intercept you in this moment. They may choose to use their special ability if it helps them. Players have the different ways they can steal the win away from you in this moment. (Kill their whole team, special ability that steals items, movement x2 tile, etc)

__Combat portion__
1. When combat is initiated, the team leader is put in the front and they are the ones to take damage. (In the case of an encountered enemy, they are automatically the team leader).
2. Add up the speed of all of your characters and if the total speed of your team exceeds the speed of the opposing team, you go first. (This is where the speed buff comes into play).
3. A turn begins. One of your characters attack the opposing team lead. You can select any of your character cards. Damage is determined by a dice roll based on your attacking character's ATK. For every ATK point, roll a dice and add up for total damage. The opposing player's team lead uses the same logic to counter some of that damage using their DEF stat. (Say atk=3, rawDMG is 13. Opposing player def=2, counteredDMG is 7. totalDMG=rawDMG-counteredDMG.)
4. Before attacking, you can use an item or use your special ability. An item like the sword will raise your atk by 1 making you do more damage. A special ability may allow you to attack twice. You can only use 1 item and 1 special ability per turn. And stats cap at a certain point.

---

## **Example Round**
1. Player 1 recieves three unique cards and adds to team.
   - Selects tile to move to. Turn ends.
2. Player 1 and 2 cycle through moving along the board.
3. Every few tiles they will pull an event card. Event card may get them a key and win the game or do something else.
4. If player found key or other team is dead, player wins.


