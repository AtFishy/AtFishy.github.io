### Dynamic Difficulty Adjustment in a Souls-Like combat System
## About

This project was made to tackle and play around with one of the biggest issues with Souls-Like games in my view. The issue of players finding the combat or gameplay so difficult, they will stop playing. Souls-Like games often have deep and very intriguing stories that creators have spent hours upon hours working on and detailing, just for players to not be able to experience it because one boss was maybe too difficult. Though some people might argue that just adding a difficulty setting to the game would fix this, it also kills the spirit of the genre, and can open the player up to ridicule from others as they didn't have as high a difficulty as someone else. It might also just dissuade some people from the game altogether as they're playing only for the challenge. Due to these reasons, I wanted to try adding a dynamic difficulty adjustment system to a Souls-Like combat system. Changing the boss's difficulty on the fly, responding immediately to the player's performance could reduce a lot of the frustration some people experience, and allow them to keep playing what could be an interesting and amazing game. 

There were two approaches to this. Adjusting a boss's difficulty during the fight, or adjusting between attempts. I chose to go with the former as it could make for interesting techniques in regards to the behaviour of the enemy. For example, if the player was doing well and the difficulty was to be adjusted higher, this could causes a behavioural change in the enemy where it gets angrier that it is being beaten so easily. Contrastly, if the play does bad and the difficulty needs to adjust to help them a little, the enemy could start getting cocky, or decide to "toy" with them a bit, giving the player more openings for attacks or healing. Choosing this approach also means that the player is less likely still to get frustrated. Needing the player to die for the adjustment to kick in could meant that the player has to die a lot for the fight to get to a level that they could complete it. 

As the focus of this project was to toy with the behaviour of the enemy and calculation of the adjustment, the combat system is not very refined. It is serviceable in that the player can attack and both the player and the enemy can die, but it is not as smooth or polished as I would make it if this was a much bigger scale project. 

## Adjustment Mechanic

Before I could work further on this, the metrics to calculate the adjustment needed to be chosen and the mechanics to adjust needed to be chosen.
# Metrics
- Consecutive damage the enemy has landed without being hit
- Consecutive damage the player has landed without being hit

# Mechanics
- Animation speed of enemy's attacks
- Attacks that the enemy uses
- Aggressiveness with which the enemy pursues the player
