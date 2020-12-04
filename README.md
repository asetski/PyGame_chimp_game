# PyGame chimp.py edited by Mikalai Asetski

Images, sounds and background music stored at the same directory inside folder named data. 
To puase the game use SPACE key 

## make screen bigger(5)

create global variables: 
: -SCREEN_WIDTH = 500
* SCREEN_HEIGHT = 500

during screen initialization at main loop applied desired size:
* screen = pygame.display.set_mode((SCREEN_WIDTH, SCREEN_HEIGHT))

## make monkey move around the outer edges of the window(10)

I created move_around_edge() method inside Chimp class that simulates this type of motion whenever it is called inside main loop

