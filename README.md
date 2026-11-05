# Collect And Avoid
## An UE5 project where player moves around an arena, collects coins and avoids an enemy that patrols and chases

### Setup
Because of my weak device, this project was created with Scalable Quality Preset  
Dynamic Global Illumination Method is set from Lumen to None  
Reflection Method is set from Lumen to None  
Shadow Map Method is set from Virtual Shadow Maps to Shadow Maps  

### Part 1
Changed movement paramteres:  
Jump Velocity from 500 to 1250  
Gravity Scale from 1.0 to 2.0  
Air Control from 0.35 to 0.75  

### Part 2
The "Cast To BP_Hero" module in the is needed to check the collision with hero only. Otherwise the points would be added every time the coin toches something. For example if i would like to spawn coins overtime, that drop on the floor or something like that, points would be added right after the coin touches the ground. Another example is the Enemy, if it would touch the coin without the "Cast To BP_Hero", the points would added as well
