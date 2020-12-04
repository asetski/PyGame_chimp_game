# PyGame chimp.py edited by Mikalai Asetski

Images, sounds and background music stored at the same directory inside folder named data. 
To puase the game use SPACE key 

## make screen bigger(5)

create global variables: 
* SCREEN_WIDTH = 500
* SCREEN_HEIGHT = 500

during screen initialization at main loop applied desired size:
* screen = pygame.display.set_mode((SCREEN_WIDTH, SCREEN_HEIGHT))

## make monkey move around the outer edges of the window(10)

move_around_edge() method created inside Chimp class that simulates this type of motion whenever it is called inside main loop. (called during medium level game) Add additional variable horizontal inside  Chimp class to alternate from vertical and horizontal movements. 


1. def _move_around_edge(self):
2.      "move the monkey around the outer edges"
        if self.horizontal:
            self.rect = self.rect.move((self.move, 0))
            if self.rect.left < self.area.left or \
                self.rect.right > self.area.right :
                self.rect = self.rect.move((0, self.move)) 
                self.horizontal = False
        else:
            self.rect = self.rect.move((0, self.move)) 
            if self.rect.top < self.area.top+20 or self.rect.bottom > self.area.bottom:
                self.rect = self.rect.move((-self.move, 0))
                self.image = pygame.transform.flip(self.image, 1, 0)
                self.move = -self.move
                self.horizontal = True   
 
 
 ## keep score (hit and misses) and display on screen cleanly and clearly - your design (10)
 
Inside main method before main loop created and initialize to 0  two local variables: count_punch and count_miss. 
* count_punch = 0 
* count_miss = 0

After that incriment them every time the event (hit/miss) taken place inside main loop.
3.  "elif event.type == MOUSEBUTTONDOWN:"
               if fist.punch(chimp):
                    background_music.stop()
                    punch_sound.play() #punch
                    chimp.punched()
                    count_punch += 1
                else:
                    background_music.stop()
                    whiff_sound.play() #miss
                    count_miss += 1

Then display everything. 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
