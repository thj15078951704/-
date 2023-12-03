import pygame
import random

#初始化游戏
pygame.init()

#游戏窗口大小
window_width = 800
window_height = 600

#定义颜色
white = (255, 255, 255)
black = (0, 0, 0)
red = (255, 0, 0)

#创建游戏窗口
window = pygame.display.set_mode((window_width, window_height))
pygame.display.set_caption("贪吃蛇游戏")

#蛇的初始位置和大小
snake_size = 20
snake_x = window_width // 2
snake_y = window_height // 2

#蛇的移动速度
snake_speed = 10

#食物的初始位置和大小
food_size = 20
food_x = round(random.randrange(0, window_width - food_size) / 20) * 20
food_y = round(random.randrange(0, window_height - food_size) / 20) * 20

#蛇的身体列表
snake_body = []
snake_body.append([snake_x, snake_y])

#游戏结束标志
game_over = False

#控制游戏循环
clock = pygame.time.Clock()

#游戏主循环
while not game_over:
   #处理事件
   for event in pygame.event.get():
       if event.type == pygame.QUIT:
           game_over = True
       elif event.type == pygame.KEYDOWN:
           if event.key == pygame.K_LEFT:
               snake_x -= snake_size
           elif event.key == pygame.K_RIGHT:
               snake_x += snake_size
           elif event.key == pygame.K_UP:
               snake_y -= snake_size
           elif event.key == pygame.K_DOWN:
               snake_y += snake_size

   #判断是否吃到食物
   if snake_x == food_x and snake_y == food_y:
       food_x = round(random.randrange(0, window_width - food_size) / 20) * 20
       food_y = round(random.randrange(0, window_height - food_size) / 20) * 20
       snake_body.append([food_x, food_y])

   #更新窗口背景
   window.fill(black)

   #绘制食物
   pygame.draw.rect(window, red, [food_x, food_y, food_size, food_size])

   #绘制蛇的身体
   for segment in snake_body[:-1]:
       pygame.draw.rect(window, white, [segment[0], segment[1], snake_size, snake_size])

   #绘制游戏结束标志
   if snake_x == snake_body[0][0] and snake_y == snake_body[0]
 
