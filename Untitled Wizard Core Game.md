
## Story Objectives
The overall objective of this game is for the player to escape from the pocket dimension that they are trapped inside. There are messages and resources left by other adventurers who have perished in this dimension. The main story of this game will be told by these messages.

## Design Objectives

This game seeks to be a Survival Craft game where the player will seek to progress through biomes unlocking new Survival Craft recipes and spells.

The Feeling and visuals of this game are WIZARD CORE. The environment should feel whimsical in a fantasy way. The player is expected to die frequently but death will not be too punishing beyond loosing gear. 

Gameplay is based on other Survival Craft games, namely Valheim where progression is based on unlocking biomes. 
## Gameplay Features
The game is a third person 3/4 perspective with an inventory and equip system. 
We will want to make a simple character creator that matches the vibe, but will use a generic model at first

### Inventory
The player will have a grid of items that can be held along with a carry weight. Items in a hot bar that can be selected with number keys to equip which item is active and being used. If a player exceeds the max carry weight their movement speed will be severely reduced and all recovery rates of ANY stat drop to 0 until their carry weight goes down again. We will have a fixed carry weight but it can be manipulated with spells, potions, and some items.
##### Equipping
A character can equip clothes, weapons, tools, jewelry. Anything that one would expect from a survival craft game. Armor and weapons will need to be able to be added to the character. This being a wizard game we will need to keep in mind that the cloth physics on robes and hats will be considered carefully.  The character will have the following slots for armor and weapons
* Hands (Left and Right)- Some weapons take both
* Head - Hats/Helmets
* Chest - Robes/Breastplate armor
* Legs - Pants/Greaves
* Feet - Shoes/Boots
* Rigs(Left and Right Hand)
* Amulet
  
An weapon or tool equipped in a Hand slot will be used by Right/Left click or Right left Trigger. Blocking with a shield in the offhand is L or Right click as an example
  
Activating an item in your inventory will 'Use' that item so it will drink the potion or equip the weapon(unequipping anything that might already be equipped).
All worn or equipped items still count to the carry weight of the character.
### Character Attributes
 ***Skills*** are things that the character does. Doing them increases a players skill. Having a skill gives bonuses with those actions. Mostly they reduce the stamina cost, but some can unlock passive abilities(TBD). Skills go from 1-100. Anything that the player does that is NOT tied to a skill should be flagged for farther review.
#### Skills
* Sword
* Axe
* Bow
* Spear
* Staff
* Wand
* Potions
* Rune Scrawling
* Run
* Jump
* Swim
* Pilot
* Ride
* Cook
* Build
* Forage
* Tame
### Stats
* Health
* Stamina
* Focus
* Satiety
* Movement Speed
* Armor
* Stamina Efficiency
* Toughness
* Jump Height
* Carry Weight
* Health Regen
* Stamina Regen
* Focus Regen
* Satiety Decline
  
## Things that Can effect the character
All things that effect the character effect their stats. These should be applied like tags. Each will be visible on the players Hud. Some will effect the player camera via post process or other effect.
### Statuses
* Rested - Bonus to stamina, health, and focus regen
* Sheltered - No stat changes but allows for sleeping and resting
* Wet - Penalty to Stamina Regen
* Cold - Penalty to Stamina and Focus Regen
* Hot - Penalty to Stamina and Focus Regen
* Burning - Damage over time
* Stunned - Slows movements and actions
* Frozen - Stops movements and actions
* Intoxicated - random input location drift, focus penalty, Toughness Bonus, Camera effect
* High - Camera effect, focus penalty, meta effect for some spells
* Hallucinating - Camera effect meta effect for environment and spells
* Asphyxiated - Damage over time - caused by smoke some environment elements
* (Leave room for more)
  
## Food
A very important part of the game is food and cooking the player should consider what their next meal will be. Want to collect recipes and find/harvest/cultivate new ingredients.

### Eating
#### Satiety
The player will have a Satiety meter that declines over time

#### Stay
Each food item has a stay that determines how many *Ticks* a food item will last. Each tick all bonuses and Satiety decline relative to the ramaining stay/maxstay.ie
  A carrot could have Satiety = 6, *All Bonuses* = 3, Stay =6. If we loose 1 Stay each 20 second tick, then after a minute we would  current Stay /max Stay = 3/6 so we would have a Satiety of 3 added, all bonuses of 1.5 
  
To eat food the player must have Satiety to eat the entire item

#### Food Stats
* Satiety
	Amount of Satiety that gets added to the meter
* Stay 
	  How long does this effect last
* Health Bonus
* Stamina Bonus
* Focus Bonus
* Other Bonuses/Tags

  
### Cooking

#### Recipes
Items can have a tag Ingredient, that ingredient will have sub-tags listed bellow. Placing matching tags into the recipe will allow the player to make that food. The stats of a produced item will be the sum of the ingredients * recipe modifiers for each stat + any bonus effects from the ingredients
 Recipes are unlocked in a work station. More can be unlocked by upgrading a cook station.
 Recipes should be stored in a Data Table with Name, Ingredient Tag Combo that supports optional ingredients, the stat modifier array, and crafting station to make, and crafting station level to unlock

example: 
	**Sandwich** = Bread + Protein + At Least one(Veggie + Cheese + Sauce) 
			    Satiety= 0.5
			     Stay = 2
			     Health = 1.5
			     Stamina = 1.5
			     Focus = 1
	Making a White bread(Satiety = 5 All stats =1 for simplicity) + Chicken( Satiety = 6 All Stats=5) and Carrot(Satiety = 6 All Stats =3)
	 Resulting Chicken Carrot Sandwich = 
		 Satiety = 8
		 Stay = 18
		 Health = 13.5
		 Stamina = 13.5
		 Focus = 9
	 If the Carrot were to have a skill bonus or other effect then that would apply to the sandwich as well.
#### Ingredient tags
* Veggie
* Bread
* Starch
* Protein
* Fruit
* Legume
* Cheese
* Oil
* Sauce
* Liquid
* (Room for More)

## Crafting and Building
### Building
Core to the gameplay Building will be done with a building tool, A hammer, or other equipped implement tagged with building tool. Equipping and opening a context menu that shows all known build recipes selecting the recipe will show a ghost version of the build. If the player has the required resources, either in an inventory or in a chest within build range they can immediately create the structure. Additionally, build recipes require a crafting station. Wood wall requires a workbench. Stone requires masonry station etc. 

#### Build sockets
The Structures that the player builds should be able to lock together to give the feel of locking pieces together. Each build component will have sockets that can other build components can lock to with their sockets. We will give more control and features with building after the initial prototype 
#### Build recipes
Initially the player will have no recipes but as they collect items in the world keep track of what they picked up. when they have all required resources to craft a build piece they get a notification that that build recipe is unlocked. They need to have collected all required ingredients and have built the required workstation.
#### Structure score
To limit the height of builds a built piece needs to have structural integrity. When placing a build piece on any surface that surface Structure score is accounted for and the built piece has a score that is lower than the built score based on its structural strength(0-1) which gets set in a data table. If a placed piece is less than or equal to 0.1(Global variable that we can tune) after being placed it will break and drop its ingredients.
For example a wooden wall has a structural strength of 0.7 so if placed on solid ground its Structural score is 0.7. A wall placed on top of it = 0.7*0.7 = 0.49. 

This score should be visible to a player in build mode. When they are showing the ghost mesh of the piece they want to build. there should be a shader that highlights the base mesh and is Green for a solid base and Red for a weak one, with Yellow in between. 

#### Vehicle Chassis
A special kind of build piece is a vehicle chassis that can support SOME builds on top of it, but should be very limited. The best example of this will be the cart. It starts with its own structural integrity an can have other components added to it. The player can pull the cart themself or can build a yoke to attach to *tamed* creatures to apply power. They can be controlled via driver seat. Creatures will keep pulling and follow the clearest path in front of them if they are not being steered by the player. 
##### Types of vehicles
* Cart - Pulled by animals with yokes. Allows building on
* Plow - pulled by animals tills fields very efficiently
* Sled - pulled by animals major movement bonus on snow
* Rowboat - small boat manual labor required
* Sailboat - small boat uses the wind to maneuver
* Galley - medium boat, difficult to use alone, uses wind to maneuver - Allows building on
* Hot air balloon - burns fuel to rise, flies, pushed by wind
* Mechanical legs - burns COAL to move, higher tech(Expensive) - allows building on

### Crafting
The player can build crafting stations and then interact with them, interacting will give them access to *Crafting recipes* that are items that when crafted are placed into the players inventory. This is how all food, weapons, armor, potions, and anything that can fit in an inventory that isn't a raw material is made.(Some are found in the world but those are special cases)

All Items should have a recipe that links to a crafting station, or a place in the world it gets spawned or dropped. 

#### Crafting Levels
Crafting stations can be upgraded by building crafting upgrades that are build pieces in the world that cost resources, if they are in range of a crafting station they will increase the level of that station increasing the number of known recipes. 

### Farming
Many ingredients and raw food items can be grown in *plots*. A *seed* can be placed into a plot, if growing conditions are met. After some time, Demined by the seeds *growth time*  a crop matures and can be harvested. A crop drops ingredients at fixed drop rate when harvested.

#### Plots
* Cultivated land --- Dirt that the player has *tilled* and is close to water
* Pot --- Indoors functions like Cultivated land
* Hydroponic pot --- Indoors, advanced and requires some magic. Bonus to some crops
* Mushroom Bolt --- Will grow wood eating mushrooms
* Spore Urn --- Will grow manure mushrooms

## Taming
Animals with a *tamable* tag can be tamed. to tame an animal they must be *Happy* and within a player tick. That increases their *Tame score* once a wild creatures tame score goes from 0 to 100 they are tamed. A creature that is bred from two tamable creatures is tame.

Tamable creatures states:
* Happy
* Afraid
* Hungry
  
Tamable creatures will have an item list of items they will eat.

##### Tamable creature templates
* Passives (Chicken, Quail, Dove)
	* Non aggressive
	* Drop Eggs
	* Ok drops on death
	* Easy to breed/maintain
	* Cannot be attached to Saddle or Yoke
* Passive Bovine(goat, alpaca, cow)
	* Non aggressive
	* Provide drop when interacted with proper tool
	* Some have valuable drops on death
	* Can attach Yoke(L1)
	* Cannot attach Saddle
* Burden/Mount(Horse, Mule, Camel, Ostridge)
	* Non aggressive
	* very cheap/non beneficial drops on death
	* Attach Yoke(L2)
	* Attach Saddle
* Large Burden(Buffalo, Ox)
	* non aggressive
	* High drops on death
	* Attach yoke L3
	* Attach Saddle
* Flying( magpie,Raven, Owl)
	* Non aggressive
	* Poor drops on death
	* Provides passive loot
	* Intended for familiars
* Guards(Wolf, Dog, Cougar)
	* Aggressive
	* Medium drop on death
	* Attach Yoke(L2)
	* Cannot attach Saddle
	* Defends player
* Large Guard - Bear
	* Aggressive
	* Defends player
	* High drops on death
	* Attach Yoke (L3)
	* Attach Saddle
For the initial prototype with will have one of each category. The first listed in the parens is what I intend to start with.

### Equipment for Animals
#### Yoke
Attached to a animal a Yoke allows for a creature to be attached to a vehicle and pull it. Yokes L1-L3 determine how much force is applied to the vehicle/cart and how much stamina each creature has
#### Saddle
Attach to an animal to make them a mount. They are their own vehicle and can be ridden.

## Combat
The world will have hostile enemies in all biomes. The players main challenges will be to deal with more numerous and powerful foes.    