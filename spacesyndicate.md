# Shadowstar Syndicate
### About
This is vibe code game in html,css,js about running space criminal syndicate and sabotaging Galactic Republic so they dont catch us. 
*Story:* We are Shadowstar Syndicate a small aspiring crime organization in space full of ambitious, young and dynamic enterprenurs with elastic aproach to law. 
We are smuggling illegal goods. And organizing underground Monster Mash fights. Maybe piracy in the future. 

## The GRAND VISION
I see my game great and beautiful full of features. So many feautures they collapse into singularity. Generally it will be asymetric boardgame, where player is crime lord in space. 
We play Jabba the Hutt but without royalities. And we build our empire. And we need to sneak under radar of Galactic Republic, we can corrupt them, bribe officials, support insurgence to keep them busy. 
Our end goal is to promot crypto bro as chancellor to defund police, maybe start galactic civil war and sell arms to both sides. But that is future feature. 

### Minimal Working Version
So far the game is 3 buttons and the dream. 

## Game loop
This is turn based game. There is no limit so far. What we can do:
+ Buy facility
+ Dispatch agents on mission
+ Bail out agent if they are catched
+ We manage allertness

## Buy facility
We can buy:
**Cantina** 100c, gives +5c each turn flat. No limit. 
Yes, it is possible we just turn into galaxy wide cantina chain, the smuggle is too much hustle and risk for what it is worth.
**Monster Arena** 1000c, +100c a turn, we need capture 2 monsters first. 

## Agents and Mission
We have... 1 agent. Each turn we can send our agent on 1 mission. 
**Nemo** captain of freighter Nostromo. It is bigger in the inside, believe me. And Nemo is tentacle girl. 
Stats: Sneak 3, Charm 2, Power 1, Organization 1, HP 3

** Bail Out ** If Agent is captured we can always bail them for 100c, if agent is captured and we dont have 100c we loose the game. 

## Missions
We ave 3 mission to choose from at the time. Each have timer of 3-9 turns of avaibility, after which it drops. We could drop any number of mission, and we will get new one but next turn. 

### Smuggle
Risk 1-5 Sneak
We smuggle goods from planets to planets. Pays 20-100c depending on risk.

### Raid
Risk 1-5 Power
We commit haist to steal something. Pays 30-150c. But double chance for discovery by space police.

### Bribe officials
Risk 1-5 Charm
We need 100c to lower allertness by 1, but then reduce 20-100% of that payment depending on difficulty. Half risk to be discovered. 

### Monster Hunt
Risk 3-5 Power
We can catch giantic monster as our pet. We need 2 monster for Undergroudn Pit fight. 

### Recruit Goons
Risk 1-3 Charm
We recruit extra muscle giving Nemo Goon item for +1 Power. We can have multiple goons. 

### Organize Cantina Network
Risk 1-3 Organization
We get extra 5-15c for each cantina we have. 


## Alertness
Life would be cool if not Space Police. They have alert levels ranging from 0 to 5. Each level gives level level * 10% chance to be catched during mission. When we are catched we can perform Bluff, Shoot, Hide, Defend action. 
Bluff: Charm, Shoot: Power, Hide: Sneak, Defend: Oranization 
If we fail we are jailed and need 100c to bail out. 

## Test
We roll n d6 where n is our characteristic. and 4,5,6 is score. We need to meet equal or more target. Rolling 6 gives +1 point. Getting double points over required gives us +50c as bonus and some fluff text. 

## Win Con
We win turn after we build Monster Mash Arena Pit. Which gives us stable incom and entertaiment for life. 




