# Dynamic Difficulty Adjustment in a Souls-Like combat System
## About

This project was made to tackle and play around with one of the biggest issues with Souls-Like games in my view. The issue of players finding the combat or gameplay so difficult, they will stop playing. Souls-Like games often have deep and very intriguing stories that creators have spent hours upon hours working on and detailing, just for players to not be able to experience it because one boss was maybe too difficult. Though some people might argue that just adding a difficulty setting to the game would fix this, it also kills the spirit of the genre, and can open the player up to ridicule from others as they didn't have as high a difficulty as someone else. It might also just dissuade some people from the game altogether as they're playing only for the challenge. Due to these reasons, I wanted to try adding a dynamic difficulty adjustment system to a Souls-Like combat system. Changing the boss's difficulty on the fly, responding immediately to the player's performance could reduce a lot of the frustration some people experience, and allow them to keep playing what could be an interesting and amazing game. 

There were two approaches to this. Adjusting a boss's difficulty during the fight, or adjusting between attempts. I chose to go with the former as it could make for interesting techniques in regards to the behaviour of the enemy. For example, if the player was doing well and the difficulty was to be adjusted higher, this could causes a behavioural change in the enemy where it gets angrier that it is being beaten so easily. Contrastly, if the play does bad and the difficulty needs to adjust to help them a little, the enemy could start getting cocky, or decide to "toy" with them a bit, giving the player more openings for attacks or healing. Choosing this approach also means that the player is less likely still to get frustrated. Needing the player to die for the adjustment to kick in could meant that the player has to die a lot for the fight to get to a level that they could complete it. 

As the focus of this project was to toy with the behaviour of the enemy and calculation of the adjustment, the combat system is not very refined. It is serviceable in that the player can attack and both the player and the enemy can die, but it is not as smooth or polished as I would make it if this was a much bigger scale project. 

## Adjustment Mechanic

Before I could work further on this, the metrics to calculate the adjustment needed to be chosen and the mechanics to adjust needed to be chosen.
### Metrics
- Consecutive damage the enemy has landed without being hit
- Consecutive damage the player has landed without being hit

### Mechanics
- Animation speed of enemy's attacks
- Attacks that the enemy uses
- Aggressiveness with which the enemy pursues the player

## Implementation of Animation Rate Change

![Image](/images/DDASoulsLike/DDASoulsLikeImage1.png)

This is the maths logic for how the difficulty is calculated. A log function is used purely because they provide nice gradual increases over time, which is key with this as you don't want to clue the player in too much to what's happening. 
After this is calculated, the value is plugged straight into the 'Montage Set Play Rate' action. This saves the global animation rate from being changed which would cause the enemy's movement to look a bit odd which we don't.

![Image](/images/DDASoulsLike/DDASoulsLikeImage2.png)

Below are two gifs demonstrating the animation rate change when playing the project. Notice how as the health of the respective entities decreases, the animations of the enemy speed up and slow down. I've used a keybind to activate the health change to demonstrate it, but in a game, this would be done when the player takes a hit or lands a hit. 

![Image](/images/DDASoulsLike/DDASoulsLikeWEBP1.webp)

![Image](/images/DDASoulsLike/DDASoulsLikeWEBP2.webp)

## Implementation of Enemy Behaviour

![Image](/images/DDASoulsLike/DDASoulsLikeImage3.png)

This is the important section of the behaviour tree of the enemy. The behaviour will check what the current value of the difficulty scale is, and execute the correct string of actions based on the value. 

This is far from a complete behaviour tree that would be implemented in a full game, but it demonstrates the idea behind the dynamic difficulty adjustment. Lower difficulty, the enemy will be more passive, have less variety in attacks and overall give the player a more relaxed experience. Higher difficulty (and also default difficulty in this demo), the enemy would have a higher variety of moves, close the gap to be closer to the player and have less obvious openings, giving the player a more tense and difficult experience. 


## Summary

This project felt like a big learning experience. Mostly learning to use Unreal again and derusting after a while. I am fairly happy with this, but it's obviously not perfect. There are glitchy animations because of the play rate of the montages. The behaviour tree is not as complex as it could be. If I came back to this project, expanding the behaviour tree and refining the animations would be the most important parts. 

When going back to this to get videos to add to this page, I found a very annoying thing to do with the "Montage Set Play Rate" action. It only changes the play rate of the montage if it is currently playing. It doesn't change it definitively for the montage. Therefore, the only way to really implement this would be to set the play rate at the start of the montage playing, every time a montage is played. This would be a lot of hassle for this small project, so I used a workaround using the "event tick" to set the montage play rate every tick. This is horrible practice for performance, but it works to demonstrate the point of the project.
