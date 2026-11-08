# Collect And Avoid

# An Unreal Engine 5 project where player moves around an arena, collects coins and avoids an enemy that patrols and chases

**Engine Version:** 5.8.4

### Showcase video:
[(Link)](https://youtu.be/pDpopPaOG1A)

### How to run the game:
  1. Download the CollectAndAvoid_ta1lw1nd.zip archive from this link:  [(Link)](https://drive.google.com/file/d/1Sx5g4XpFw3VfJovLa0gJVbG9uok5Dvnb/view?usp=drive_link)
  2. Extract the files
  3. Open the .exe file

### Controls:
- WASD - move
- Mouse - look
- SPACE - jump
- LSHIFT - sprint
- ESCAPE - pause

## Short description of each Blueprint

**Core**

- **BP_Coin:** a collectible. Its mesh rotates every frame. When it overlaps BP_Hero, it plays a sound, spawns FX and calls the AddScore function in BP_GameState.
- **BP_Hero:** a modified copy of the preset Third Person character. It creates the HUD widget and the background loop music, and contains the sprint logic.

**Enemy**

- **ABP_Enemy:** the enemy's animation blueprint, copied and slightly modified from the Third Person character.
- **BP_Enemy:** the enemy character that chases the player. The lose logic is stored here.
- **BP_EnemyAIController:** the enemy's "brain". The AI Sight logic is stored here.
- **BP_PatrolPoint:** a patrol point for the enemy.
- **BB_Enemy:** the enemy's blackboard.
- **BT_Enemy:** the enemy's behaviour tree.
- **BTT_NextPatrolPoint:** a custom task that picks the next patrol point from the array of patrol points.

**Game**

- **BP_GameMode:** the custom game mode. It contains no logic.
- **BP_GameState:** stores the score and the game state. Almost all of the game logic is placed here.

**FX**

- **NS_CoinPickup:** a Niagara System created from the Fountain preset and slightly modified.
- **BP_CameraShake:** a simple camera shake blueprint.

## Development breakdown
### Setup
Because of my weak device, this project was created with Scalable Quality Preset  
Dynamic Global Illumination Method is set from Lumen to None  
Reflection Method is set from Lumen to None  
Shadow Map Method is set from Virtual Shadow Maps to Shadow Maps  

### Part 1
Changed movement parameters:  
Jump Velocity from 500 to 1250  
Gravity Scale from 1.0 to 2.0  
Air Control from 0.35 to 0.75  

### Part 2
The "Cast To BP_Hero" module in the is needed to check the collision with hero only. Otherwise the points would be added every time the coin touches something. For example if i would like to spawn coins overtime, that drop on the floor or something like that, points would be added right after the coin touches the ground. Another example is the Enemy, if it would touch the coin without the "Cast To BP_Hero", the points would added as well

### Part 4
The WBP_HUD updates by the custom OnScoreChanged that is triggered in the AddScore function on the BP_GameState. It triggers only when the score changed. I chose this method because it doesn't require updating the score text every frame  

### Part 5
Almost the entire frame rendering time (Around 12.5 ms) is taken up by the rendering process itself. There are no heavy nodes in the project that are being called every frame

Two actions feedback:
  1. The coin creates simple NiagaraSystem when taken by the player
  2. Tha player`s camera shakes when Enemy sees BP_Hero

### Asset list
| Asset | Used for | Source | Licence |
|---|---|---|---|
| Third person template (character, mannequin, animations, input assets) | BP_Hero, ABP_Enemy, BP_Enemy | Unreal Engine Third Person template (Epic Games) | Unreal Engine EULA |
| Collect sound | Coin pickup | Created by me | Own work, no restrictions |
| Chase sound | Enemy starts chasing | Created by me | Own work, no restrictions |
| Background music loop | Music in BP_Hero | Created by me | Own work, no restrictions |

All sounds were created by me from scratch: the collect and chase sounds, as well as the background loop were created in **FL Studio**
