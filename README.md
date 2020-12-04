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

move_around_edge() method created inside Chimp class that simulates this type of motion whenever it is called inside main loop
1. def _move_around_edge(self):
2.       "move the monkey around the outer edges"
3.        if self.horizontal:
4.            self.rect = self.rect.move((self.move, 0))
5.            if self.rect.left < self.area.left or \
6.                self.rect.right > self.area.right :
7.                self.rect = self.rect.move((0, self.move)) 
8.                self.horizontal = False
9.        else:
10.            self.rect = self.rect.move((0, self.move)) 
11.            if self.rect.top < self.area.top+20 or self.rect.bottom > self.area.bottom:
12.                self.rect = self.rect.move((-self.move, 0))
13.                self.image = pygame.transform.flip(self.image, 1, 0)
14.                self.move = -self.move
15.                self.horizontal = True   

1. def _move_around_edge(self):
2.         "move the monkey around the outer edges"
3.        if self.horizontal:
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
