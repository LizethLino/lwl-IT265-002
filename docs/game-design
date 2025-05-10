## Change Log

Physical prototype had manual dice throws and selection of character cards and lead. The digital prototype has no such limitation. It automatically chooses the team leader as the character with the highest DEF. Same goes for combat sequences where it selects out of the alive characters and picks the character with the highest ATK.

As I was making my digital prototype it occured to me that during an event turn a player may want to see their character cards to see if 

Added a collapsable UI element that displays Debug.Log to show the prints to console as the game plays. Added this after I realized that the debug.Log technically isn't a part of the meaning the webGL deployment was very bare without it.

---

## Game Title: System Failure
## Game Genre: Strategy RPG
Game Demo WebGL Link: https://lizethlino.github.io/lwl-IT265-002/SystemFailureGame/Ver3/
Video Demo Link: https://www.youtube.com/watch?v=W92Aafsofy0
---

## Objective
- Find the key first or be the last team standing.

---

## Core Features
- Player Tile Movement
- Tile types
- "HomeAdvantage" Speed Buff (Not Implemented)
- Player team cards
- Encounter enemy combat
- Pull item add to inventory
- Use item/displayed inventory (Not implemented)
- Event card effects with accept/reject function

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


