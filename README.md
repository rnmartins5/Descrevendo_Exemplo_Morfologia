# Descrevendo_Morfologia
#from https://opencv-python-tutroals.readthedocs.io/en/latest/py_tutorials/py_imgproc/py_morphological_ops/py_morphological_ops.html
#Importando a biblioteca cv2
import cv2
#Importando a biblioteca numpy e dando o nome dela como np
import numpy as np    

#A variavel img está recebendo uma imagem que é carregada pela função cv2.imread do arquivo j.png com a intensidade de cinza zero
img = cv2.imread('j.png',0)
#Aqui acontece a mesma coisa so que com o arquivo j_ruido.png
img_opening = cv2.imread('j_ruido.png',0)
#Mesma coisa, mas com o arquivo j_furos.png
img_closing = cv2.imread('j_furos.png',0)
#As variaveis estão recebendo as dimensões da imagem 
altura, largura = img.shape
#A variavel Kernel está recebendo uma matriz 5x5 de 1
kernel = np.ones((5,5),np.uint8)
#Retorna na tela a variavel Kernel
print(kernel)
     

erosion = cv2.erode(img,kernel,iterations = 2)
dilation = cv2.dilate(img,kernel,iterations = 2)
     

gradient = cv2.morphologyEx(img, cv2.MORPH_GRADIENT, kernel)
opening = cv2.morphologyEx(img_opening, cv2.MORPH_OPEN, kernel)
closing = cv2.morphologyEx(img_closing, cv2.MORPH_CLOSE, kernel)
     

'''
#Caso usa com Python no próprio computador
cv2.imshow('in', img)
cv2.imshow('erosion_out', erosion)
cv2.imshow('dilation_out', dilation)
cv2.imshow('opening_out', opening)
cv2.imshow('closing_out', closing)
cv2.imshow('gradient_out', gradient)
'''
#Caso use o Google Colab
cv2_imshow(img)
cv2_imshow(erosion)
cv2_imshow(dilation)
cv2_imshow(opening)
cv2_imshow(closing)
cv2_imshow(gradient)
     
