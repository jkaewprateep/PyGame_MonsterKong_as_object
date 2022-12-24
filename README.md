# PyGame_MonsterKong_as_object
For working and study with PyGame Monster Kong game

## Game input libraries ##

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
 
```
game_console = MonsterKong_Game()
p = PLE(game_console, fps=30, display_screen=True, reward_values={})
p.init()

obs = p.getScreenRGB()
```

## Game test running ## 

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

