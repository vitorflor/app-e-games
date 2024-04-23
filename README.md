import pygame, sys
pygame.init()

largura_janela = 800   
altura_janela = 600
pygame.display.set_caption('Game da tai')
clock = pygame.time.Clock()
fgExit = False
personagemImg = pygame.image.load('taicerta.png')
cenario = pygame.image.load('bailão.png')
tela = pygame.display.set_mode((largura_janela, altura_janela))
x = (largura_janela * 0.1)
y = (altura_janela * 0.1)
x1 = 0
x2 = 0
y1 = 0
y2 = 0
personagem_speed = 0

somdefundo = pygame.mixer.music.load('ritmada do zelda.mp3')
pygame.mixer.music.set_volume(0.30)
pygame.mixer.music.play(-1)

while not fgExit:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            fgExit = True
        if event.type == pygame.KEYUP:
            if event.key == pygame.K_a:
                x1 = 0
            if event.key == pygame.K_d:
                x2 = 0
            if event.key == pygame.K_w:
                y1 = 0
            if event.key == pygame.K_s:
                y2 = 0
        if event.type == pygame.KEYDOWN:
            if event.key == pygame.K_a:
                x1 = -5
            if event.key == pygame.K_d:
                x2 = 5
            if event.key == pygame.K_w:
                y1 = -5
            if event.key == pygame.K_s:
                y2 = 5
    x += x1 + x2
    y += y1 + y2
    tela.blit(cenario,(0,0))
    tela.blit(personagemImg, (x, y))
    pygame.display.update()
    clock.tick(60)

pygame.quit()
