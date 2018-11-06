# mouse-dodging-game
import pygame

pygame.init()

display_width = 800
display_height = 600

black = (0,0,0)
white = (255,255,255)
red = (255,0,0)

gameDisplay = pygame.display.set_mode((display_width,display_height))
pygame.display.set_caption('Mouse Trap')
clock = pygame.time.Clock()

mouseImg = pygame.image.load('ms3.png')

def mouse(x,y):
    gameDisplay.blit(mouseImg,(x,y))

def game_loop():

    x = (display_width * 0.45)
    y = (display_height * 0.8)

    x_change = 0

    crashed = False
    # while loop acting as game loop

    while not crashed:

        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                crashed = True

            if event.type == pygame.KEYDOWN:
                if event.key == pygame.K_LEFT:
                    x_change = -5
                elif event.key == pygame.K_RIGHT:
                    x_change = 5


                if event.type == pygame.KEYUP:
                    if event.key == pygame.K_LEFT or event.key == pygame.K_RIGHT:
                        x_change = 0


        x += x_change

            
        gameDisplay.fill(white)
        mouse(x,y)
        pygame.display.update()
        clock.tick(30)
game_loop
pygame.quit()
quit()
