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
 
Inside main method before main loop created and initialize to 0  two local variables: count_punch and count_miss:

* count_punch = 0 
* count_miss = 0

After that incriment them every time the event (hit/miss) taken place inside main loop:

3.  elif event.type == MOUSEBUTTONDOWN:
4.               if fist.punch(chimp):
                   background_music.stop()
                    punch_sound.play() #punch
                    chimp.punched()
                    count_punch += 1
                 else:
                    background_music.stop()
                    whiff_sound.play() #miss
                    count_miss += 1

Then display everything: 
 
5. screen.blit(background, (0, 0))
6.         punch_text = sm_font.render("Punch count: " + str(count_punch), 1, (255,0,0))
           screen.blit(punch_text, punch_text_position)       
           miss_text = sm_font.render("Miss count: " + str(count_miss), 1, (255,100,0))
           screen.blit(miss_text, miss_text_position)
           allsprites.draw(screen)
           pygame.display.flip() 
 
 ## allow user to puas the game (5)
 
To simulate the pause user must press SPACE key during game. Created four methods in order to add pause function to the game: paused(), button(), unpaused(), and quitgame(). Method paused() and unpaused() use global variable "pause" to stop and start main loop. Used additional screen buttons created with method button() to continue and to quit the game. Method quitgame() crated to stop the game. Inside main loop I added extra if else branch to check if SPACE was pressed.  


1. def paused(scr):
2.     "pause the game"
3.     global pause
4.     font = pygame.font.Font(None, 115)
    txt_position = ( 110, (SCREEN_HEIGHT/2 - 100)) 
    txt = font.render("Paused" , 1 , (0,0,0))
    scr.blit(txt, txt_position)
    pygame.mouse.set_visible(1)
    while pause:
        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                pygame.quit()
                quit()
        button("Continue", scr, 100,350,100,50, unpaused)
        button("Quit", scr, 320,350,100,50, quitegame )
        pygame.display.update()
        

def button(msg, scr, x, y, width, height, action=None):
    "creates a button on selected screen"
    mouse = pygame.mouse.get_pos()
    click = pygame.mouse.get_pressed()
    if x + width > mouse[0] > x and y + height > mouse[1] > y:
        pygame.draw.rect(scr, (255,0,0) , (x,y,width,height))
        if click[0] == 1 and action != None:
            action()         
    else:
        pygame.draw.rect(scr, (0,255,0) , (x,y,width,height))
    sm_font = pygame.font.Font(None, 20)
    txt_position = ( (x + (width/2) - 25), (y+(height/2)) )
    txt = sm_font.render(msg,1,(0,0,0))
    scr.blit(txt, txt_position)

def unpaused():
    "unpause the game"
    global pause
    pause = False





