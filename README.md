# Collect And Avoid

##An Unreal Engine 5 project where player moves around an arena, collects coins and avoids an enemy that patrols and chases

##Vesrion 5.8.4

###How to run the game:
...

###Short description to each of the Blueprints
BP_Coin: Game Object that stores and adds the score. Mesh of the coin rotates every frame and when collides with a BP_Hero it spawns sound, FX and calls the AddScore function  
BP_Hero: Modified copy of the preset third person character. The HUD widget and background loop music is created in here. Also there is a simple sprint logic
Enemy:  
  1. ABP_Enemy: animation blueprint of the enemy. Copied and slightly modified from the third person character from the presets
  2. BP_Enemy: physical character that chases player. The lose logic is stored in here
  3. BP_EnemyController: main "brain" of the enemy. The AI Sight logic is stored in here
  4. BP_PatrolPoint: patrol point for the enemy
  5. BB_Enemy: blackboard of the enemy
  6. BT_Enemy: behaviour tree of the enemy
  7. BTT_NextPatrolPoin: custom task that picks the patrol point from the array of the patrol points
Game:  
  1. BP_GameMode: custom game mode for the game. has no logic at all
  2. BP_GameState: the state blueprint of the game. Almost all of the game logic is places in here
FX:
  1. NS_CoinPickup: Niagara System that is created from the Fountain preset. Slighly modified
  2. BP_CameraShake: Simple camera shake blueprint

###Setup
Because of my weak device, this project was created with Scalable Quality Preset  
Dynamic Global Illumination Method is set from Lumen to None  
Reflection Method is set from Lumen to None  
Shadow Map Method is set from Virtual Shadow Maps to Shadow Maps  

###Part 1
Changed movement paramteres:  
Jump Velocity from 500 to 1250  
Gravity Scale from 1.0 to 2.0  
Air Control from 0.35 to 0.75  

###Part 2
The "Cast To BP_Hero" module in the is needed to check the collision with hero only. Otherwise the points would be added every time the coin toches something. For example if i would like to spawn coins overtime, that drop on the floor or something like that, points would be added right after the coin touches the ground. Another example is the Enemy, if it would touch the coin without the "Cast To BP_Hero", the points would added as well

###Part 4
The WBP_HUD updates by the custom OnScoreChanged that is triggered in the AddScore function on the BP_GameState. It triggers only when the score changed. I chose this method because it doesn't require updating the score text every frame  

Two actions feedback:
  1. The coin creates simple NiagaraSystem when taken by the player
  2. Tha player`s camera shakes when Enemy sees BP_Hero
