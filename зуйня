import random

import pygame as pg

TITLE = 'ja togo v rot jebal'
pg.init()
pg.font.init()
circle_speed = 5
circle_y_speed = circle_speed
circle_x_speed = 0
circle_first_coll = False
WIDTH = 1280
HEIGHT = 720
fps = 144
white = (255, 255, 255)
black = (0, 0, 0)
platform_width = 100

circle_radius = 15
circle_rect = pg.rect.Rect(WIDTH / 2 - circle_radius,
                           HEIGHT / 2 - circle_radius,
                           circle_radius * 2,
                           circle_radius * 2)

platform_height = 15
platform_speed = 10
platform_rect = pg.rect.Rect(WIDTH / 2 - platform_width / 2,
                             HEIGHT - platform_height * 2,
                             platform_width,
                             platform_height)
clock = pg.time.Clock()
game_over = False

screen = pg.display.set_mode([WIDTH, HEIGHT])
pg.display.set_caption(TITLE)

running = True
while running:

    if circle_rect.bottom >= HEIGHT:
        game_over = True
        circle_y_speed = -circle_speed


    screen.fill(black)

    if not game_over:


        if platform_rect.colliderect(circle_rect):
            if not circle_first_coll:

                if random.randint(0, 1) == 0:
                    circle_x_speed = circle_speed
                else:
                    circle_x_speed = - circle_speed

                circle_first_coll = True
        pg.draw.rect(screen, white, platform_rect)

        keys = pg.key.get_pressed()
        if keys[pg.K_a]:
            platform_rect.x -= platform_speed
        elif keys[pg.K_d]:
            platform_rect.x += platform_speed

    circle_rect.x += circle_x_speed
    circle_rect.y += circle_y_speed
    if circle_rect.bottom >= HEIGHT:

        game_over = True
        circle_y_speed = - circle_speed
    elif circle_rect.top <= 0:
        circle_y_speed = +circle_speed
    elif circle_rect.left <= 0:
        circle_x_speed = circle_speed
    elif circle_rect.right >= WIDTH:
        circle_x_speed = -circle_speed
    pg.draw.circle(screen, white, circle_rect.center, circle_radius)
    clock.tick(fps)
    pg.display.flip()

    for event in pg.event.get():
        if event.type == pg.QUIT:
            running = False
            continue
        elif event.type == pg.KEYDOWN:
            if event.key == pg.K_ESCAPE:
                running = False
                continue

pg.quit()
