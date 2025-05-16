import pygame
import sys

from pygame.examples.go_over_there import clock

pygame.init()

screen_width = 500
screen_height = 600

screen = pygame.display.set_mode((screen_width, screen_height))
pygame.display.set_caption("Pygame Basics")

background_color = ("green")
line_height = 150
line_width = 20
gap = 40
lines = []
car = pygame.image.load('realistic-car-illustration_23-2151227622-removebg-preview.png')
car = pygame.transform.scale(car, (80, 110))

dumb_car = pygame.image.load('bad_car.png')
dumb_car = pygame.transform.scale(dumb_car, (40, 90))
dumb_car_x = 200
dumb_car_y = 110

stupid_car = pygame.image.load('bad_car2-removebg-preview.png')
stupid_car = pygame.transform.scale(stupid_car, (80, 110))
stupid_car_x = 270
stupid_car_y = 160

pothole = pygame.image.load('hole_-_Copy-removebg-preview.png')
pothole = pygame.transform.scale(pothole, (40, 40))
potholex = 252
potholey = 287

pothole2 = pygame.image.load('hole_-_Copy-removebg-preview.png')
pothole2 = pygame.transform.scale(pothole2, (40, 40))
pothole2x = 210
pothole2y = 56

for i in range(0,screen_height, line_height + gap):
    lines.append(i)
car_x = screen_width // 2 - car.get_width() // 2
car_y = screen_height - car.get_height()
speed = 5

running = True

while running:
   for event in pygame.event.get():
       if event.type == pygame.QUIT:
           running = False
   screen.fill(background_color)
   for i in range(len(lines)):
       print(lines[i])

   pygame.draw.rect(screen,(50,50,50),(screen_width // 3, 0, screen_width // 3, screen_height))
   for i in range(len(lines)):
       lines[i] += 6

       if lines[i] > screen_height:
           lines[i] = -line_height

       pygame.draw.rect(screen,"white",(screen_width//2 - line_width//2, lines[i], line_width, line_height))
   dumb_car_y += 1
   stupid_car_y += 1.25
   potholey += speed
   pothole2y += speed
   if dumb_car_y > screen_height:
       dumb_car_y = 0
   if stupid_car_y > screen_height:
       stupid_car_y = 0
   if potholey > screen_height:
       potholey = 0
   if pothole2y > screen_height:
       pothole2y = 0

   keys = pygame.key.get_pressed()

   if keys[pygame.K_RIGHT] and car_x + 60 < 333:
       car_x+=speed
   if keys[pygame.K_LEFT] and car_x + 20 > screen_width // 3:
       car_x -= speed
   if keys[pygame.K_UP] and car_y > 0:
       car_y -= speed
   if keys[pygame.K_DOWN] and car_y + 110 < 600:
       car_y += 1

   screen.blit(car, (car_x,car_y))
   screen.blit(dumb_car, (dumb_car_x, dumb_car_y))
   screen.blit(stupid_car, (stupid_car_x, stupid_car_y))
   screen.blit(pothole, (potholex, potholey))
   screen.blit(pothole2, (pothole2x, pothole2y))

   playercar = pygame.Rect(car_x + 20, car_y + 10, car.get_width() - 40, car.get_height() - 20)
   dumbcar = pygame.Rect(dumb_car_x + 5, dumb_car_y, dumb_car.get_width() - 10, dumb_car.get_height())
   stupidcar = pygame.Rect(stupid_car_x + 30, stupid_car_y, stupid_car.get_width() - 40, stupid_car.get_height() - 20)
   pothole1 = pygame.Rect(potholex + 10, potholey + 10, pothole.get_width() - 20, pothole.get_height() - 20)
   pothole3 = pygame.Rect(pothole2x + 10, pothole2y + 10, pothole2.get_width() - 20, pothole2.get_height() - 20)

   #pygame.draw.rect(screen, "white", playercar, 3)
   #pygame.draw.rect(screen, "white", stupidcar, 3)
   #pygame.draw.rect(screen, "white", dumbcar, 3)
   #pygame.draw.rect(screen, "red", pothole1, 3)
   #pygame.draw.rect(screen, "red", pothole3, 3)

   if playercar.colliderect(dumbcar) or playercar.colliderect(stupidcar) or playercar.colliderect(pothole1) or playercar.colliderect(pothole3):
       font = pygame.font.Font(None,52)
       text = font.render("Game over!", True, "Black")
       screen.blit(text,(270,300))
       pygame.display.update()
       pygame.time.wait(3000)
       pygame.quit()
       sys.exit()

   pygame.display.flip()
   clock.tick(60)
