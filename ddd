from pygame import *
from random import *
mixer.init()
font.init()
pos_1 = (250, 250)
window = display.set_mode((700,500))
pos_2 = (500, 250)
speed_x = 2
speed_y = -1
win_height = (600)
background = transform.scale(image.load('galaxy.jpg'), (700, 500))
class GameSprite(sprite.Sprite):
    def __init__(self, picture, pos_1, pos_2, speed):
        super().__init__()
        self.image = transform.scale(image.load(picture), (80,80))
        self.speed = speed
        self.rect = self.image.get_rect()
        self.rect.x = pos_1
        self.rect.y = pos_2
    def reset(self):
        window.blit(self.image, (self.rect.x, self.rect.y))


class Player(GameSprite):
    def update_l(self):
        keys = key.get_pressed()
        if keys[K_w] and self.rect.y > 5:
            self.rect.y -= self.speed
        if keys[K_s] and self.rect.y < win_height - 80:
            self.rect.y += self.speed
    def update_r(self):
        keys = key.get_pressed()
        if keys[K_UP] and self.rect.y > 5:
            self.rect.y -= self.speed
        if keys[K_DOWN] and self.rect.y < win_height - 80:
            self.rect.y += self.speed

game = True
finish = False
run = True
clock = time.Clock()
FPS = 60
raketka1 = Player(('Raketka.jpg'), 25, 250, 3)
raketka2 = Player(('Raketka.jpg'), 600, 250, 3)
ball = Player(('ball.jpg'), 300, 250, 2)
while game:
    for e in event.get():
            if e.type == QUIT:
                game = False
    if finish != True:
        window.blit(background, (0, 0))
        raketka1.update_l()
        raketka2.update_r()
        raketka2.reset()
        raketka1.reset()
        ball.rect.x += speed_x
        ball.rect.y += speed_y
        ball.update()
        ball.reset()
        if sprite.collide_rect(raketka1, ball) or sprite.collide_rect(raketka2, ball):
            speed_x *= -1
    display.update() 
    clock.tick(60) 
