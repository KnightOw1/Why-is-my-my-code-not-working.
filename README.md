# Why-is-my-my-code-not-working.
I am using Python for coding and for some reason my code is not having my images move when i press the corresponding keys.

Here is my code:

import pygame
from pygame.locals import *
import sys
pygame.init()
colorWHITE = (255,255,255)
colorBLACK = (0,0,0)
colorRED = (255,0,0)
gameWindow = pygame.display.set_mode((800,600))
pygame.display.set_caption('Colliding Objects')
gameQuit = False
rect1 = pygame.sprite.Sprite()
rect1.rect = pygame.Rect(300,300,50,50)
rect2 = pygame.sprite.Sprite()
rect2.rect = pygame.Rect(100,100, 100,150)
gameWindow.fill(colorWHITE)
pygame.draw.rect(gameWindow, colorBLACK, rect1)
pygame.draw.rect(gameWindow, colorRED, rect2)
pygame.display.update()
while not gameQuit:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            gameQUIT = True
            pygame.quit()
            sys.exit()
# quit keys
        if event.type == pygame.KEYDOWN:
            if event.key == pygame.K_q:
                pygame.quit()
                sys.exit()
        if event.type == pygame.KEYDOWN:
            if event.key == pygame.K_ESCAPE:
                pygame.quit()
                sys.exit()
# move keys left and right
        if event.type == pygame.KEYDOWN:
            if event.key == pygame.K_LEFT:
                rect1.rect.x = rect1.rect.x - 10
            if event.key == pygame.K_RIGHT:
                rect1.rect.x = rect1.rect.x +10
# move keys up and down
        if event.type == pygame.KEYDOWN:
            if event.key == pygame.K_UP:
                rect1.rect.y = rect1.rect.y -10
            if event.key == pygame.K_DOWN:
                rect1.rect.y = rect1.rect.y +10
# collision detection        
        if pygame.sprite.collide_rect(rect1, rect2):
            rect1.rect.y = 400
            rect1.rect.x = 400
        if rect1.rect.x > 750:
            rect1.rect.x = 740
            pygame.display.set_caption('Right Collision')
        if rect1.rect.x < 1:
            rect1.rect.x = 51
            pygame.display.set_caption('Left Collision')
        if rect1.rect.y > 550:
            rect1.rect.y = 540
            pygame.display.set_caption('Bottom Collision')
        if rect1.rect.y < 1:
            rect1.rect.y = 50
            pygame.display.set_caption('Top Collision')
