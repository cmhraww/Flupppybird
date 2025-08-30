from pygame import *
from random import randint

button_rect = Rect(1200 // 2 - 100, 800 // 2, 200, 60)


init()
window_size = 1200, 800
window = display.set_mode(window_size)
clock = time.Clock()

button_font = font.Font(None, 36)

birdrect = Rect(50, 50, 40, 40)

def generate_pipes(count, pipe_width=140, gap=280, min_height=50, max_height=440, distance=650):
   pipes = []
   start_x = window_size[0]
   for i in range(count):
       height = randint(min_height, max_height)
       top_pipe = Rect(start_x, 0, pipe_width, height)
       bottom_pipe = Rect(start_x, height + gap, pipe_width, window_size[1] - (height + gap))
       pipes.extend([top_pipe, bottom_pipe])
       start_x += distance
   return pipes

pipes = generate_pipes(150)
lose = True

while True:
    for e in event.get():
        if e.type == QUIT:
            quit()
        if e.type == MOUSEBUTTONDOWN:
            if button_rect.collidepoint(e.pos):
                lose = False
                pipes = generate_pipes(150)

    text = button_font.render("Начать игру", True, "white")


    if not lose:
        keys = key.get_pressed()
        if keys [K_w]:
            birdrect.y-=20
        if keys [K_s]:
            birdrect.y+=20

    window.fill('black')

    draw.rect(window, "yellow", birdrect)

    for pipe in pipes:
        if not lose:
            pipe.x -= 10
        draw.rect(window, 'green', pipe)

        if birdrect.colliderect(pipe):
            lose = True
    if lose:
        draw.rect(window, 'yellow', button_rect)

        window.blit(text, (button_rect.centerx - text.get_width() // 2,
                           button_rect.centery - text.get_height() // 2))

    display.update()
    clock.tick(60)
