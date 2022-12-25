# PyGame_MonsterKong_as_object

For working and study with PyGame Monster Kong game, it required to access object like variables in the games by this method, class access from initail class as Python programming like.

## Key constants ##

from pygame.constants import K_a, K_s, K_d, K_w, K_h, K_SPACE

| Key Press  | value as Int | Description |
| ------------- | ------------- | ------------- |
| K_a  | 97  | Left, press Key a |
| K_s  | 115  | down, press Key s  |
| K_d  | 100  | right, press Key d  |
| K_w  | 119  | up, press Key w  |
| K_h  | 104  | hold, press Key h  |
| K_SPACE  | 32  | actions, press Key SPACE  |

## Access primary object like in Monster Kong games ##

Start from initial class ```__init__.py``` the board class ```board.py``` in stored values we need and it is the connector to other class in the game environment, Monster Kong games.

1. Direct access to the object class as they created class like python programming scripts file.
2. Access from the ```board``` class.
3. Access from shared method from ```__init__```
4. Access from MonsterKong_Game class we initail for screen and spikes objects.

```
from ple import PLE

from ple.games.monsterkong import MonsterKong as MonsterKong_Game
from ple.games import base

from ple.games.monsterkong.person import Person as Person_Game
from ple.games.monsterkong.player import Player as Player_Game
from ple.games.monsterkong.monsterPerson import MonsterPerson as MonsterPerson_Game

game_console = MonsterKong_Game()
p = PLE(game_console, fps=30, display_screen=True, reward_values={})
p.init()

for player in game_console.newGame.Players :
    ...
for Enemies in MonsterPerson_Game :
    ...
for Allies in game_console.newGame.Allies :
    ...
game_console.getScore()
    ...
```

## Game input libraries ##

We import the Python Leanring Environment and inherit calsses objects for specific object properties such as position, values and group from provided methods ```__init__```, ```object like class```, main enter ```board class```, ```shared method``` and ```game constants```.

```
import ple
from ple import PLE
from ple.games.monsterkong import MonsterKong as MonsterKong_Game
from ple.games import base

from ple.games.monsterkong.person import Person as Person_Game
from ple.games.monsterkong.player import Player as Player_Game
from ple.games.monsterkong.monsterPerson import MonsterPerson as MonsterPerson_Game

from pygame.constants import K_a, K_s, K_d, K_w, K_h, K_SPACE
```

## Game output axises ##

The game current versions does not included getState() as other sample games, we use it for extracting games variables and objects from ```Pygame``` and ```Spikes objects``` we ```created read_current_state()```.

```
def read_current_state( string_gamestate ):
		
    if string_gamestate in ['score']:
        return game_console.getScore()
		
    elif string_gamestate in ['game_over']:	# False
        return game_console.game_over()
		
    elif string_gamestate in ['fireballGroup']:
        temp = []
        for fireball in game_console.newGame.fireballGroup :
            temp.append( fireball.getPosition() )	
        return temp
		
    elif string_gamestate in ['coinGroup']:
        temp = []
        for coin in game_console.newGame.coinGroup :
            temp.append( coin.getPosition() )	
        return temp
		
    elif string_gamestate in ['player']:
        Player_Game = game_console.newGame.Players
        temp = []
        for player in game_console.newGame.Players :
           temp.append( player.getPosition() )	
        return temp
		
    elif string_gamestate in ['monster']:
        MonsterPerson_Game = game_console.newGame.Enemies
        temp = []
        for Enemies in MonsterPerson_Game :
            temp.append( Enemies.getPosition() )	
        return temp
		
    elif string_gamestate in ['lives']:
        return game_console.newGame.lives
		
    elif string_gamestate in ['allies']:
       Allies_Game = game_console.newGame.allyGroup
       temp = []
       for allies in Allies_Game :
           temp.append( allies.getPosition() )	
       return temp
		
    elif string_gamestate in ['wall']:
        Wall_Game = game_console.newGame.wallGroup
        temp = []
        for wall in Wall_Game :
            temp.append( wall.getPosition() )	
        return temp
		
     elif string_gamestate in ['ladder']:
        Ladder_Game = game_console.newGame.ladderGroup
        temp = []
        for ladder in Ladder_Game :
            temp.append( ladder.getPosition() )	
        return temp
		
    else:
        return None

    return None
```
 
## Game Environment ## 
 
Create object from class like method and initail it values and sample return of the screen observing screen colors mapped arrays.
 
```
game_console = MonsterKong_Game()
p = PLE(game_console, fps=30, display_screen=True, reward_values={})
p.init()

obs = p.getScreenRGB()
```

## Game test running ## 

Game test running with prepared ```prediction()``` method,  model training ```model.fit()``` and games return variables to ```DATA``` training with ```LABEL```, create a dataset and update method ```update_DATA( )``` with your logical requirements for the games.

```
for i in range(nb_frames):
    steps = steps + 1
	
    if p.game_over():
        p.reset_game()
        steps = 0
        lives = 0
        reward = 0
        scores = 0
		
    if ( steps == 1 ):
        print('start ... ')

    action = K_a

    reward = p.act(action)
    obs = p.getScreenRGB()
	
    scores = scores + reward
    
    DATA, LABEL, steps = update_DATA( action )
	
    ############################################################################
    print( "score: " + str( read_current_state("score") ) )
    print( "game_over: " + str( read_current_state("game_over") ) )
    print( "fireballGroup: " + str( read_current_state("fireballGroup") ) )
    print( "coinGroup: " + str( read_current_state("coinGroup") ) )
    print( "player: " + str( read_current_state("player") ) )
    print( "monster: " + str( read_current_state("monster") ) )
    print( "lives: " + str( read_current_state("lives") ) )
    print( "allies: " + str( read_current_state("allies") ) )
    print( "ladder: " + str( read_current_state("ladder") ) )
    print( "wall: " + str( read_current_state("wall") ) )
    ############################################################################
	
```

## Result image ##

#### Game play ####
![Alt text](https://github.com/jkaewprateep/PyGame_MonsterKong_as_object/blob/main/124.png?raw=true "Title")

#### Output result for our study ####
![Alt text](https://github.com/jkaewprateep/PyGame_MonsterKong_as_object/blob/main/125.png?raw=true "Title")

