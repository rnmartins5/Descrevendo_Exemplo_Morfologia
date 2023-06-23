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
     
#Aplicando a erosão na imagem 'img' com elemento estruturante 'kernel' e fazendo a repetição da erosão 2 vezes com o 'iterations=2'
erosion = cv2.erode(img,kernel,iterations = 2)
#Fazendo o oposto da erosão, está dilatando a imagem, repetindo duas vezes
dilation = cv2.dilate(img,kernel,iterations = 2)
     
#Da o contorno dos objeto na imagem
gradient = cv2.morphologyEx(img, cv2.MORPH_GRADIENT, kernel)
#Aplicando erosão seguida da dilatação, remover pequenas bolhas da imagem, ruidos
opening = cv2.morphologyEx(img_opening, cv2.MORPH_OPEN, kernel)
#Aplicando dilatação seguida de uma erosão, fechando buracos dentro do objeto, ou conectar componentes
closing = cv2.morphologyEx(img_closing, cv2.MORPH_CLOSE, kernel)
     

#Os dois exemplos é para exibir os dados da imagem
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
     
#Descrição do codigo
Nesse código está sendo feito a manipulação de imagens usando a técnica de morfologia. Se utilizando das bibliotecas cv2 e numpy para fazer a manipulação de imagens com operações matemáticas.
Primeiramente é carregada as imagens e colocadas em  ‘variáveis’ diferentes, para carregar essas imagens temos que  buscá-las nos arquivos e em seguida colocar o nome da imagem com o seu formato.
Depois é criada outras variáveis que então é colocada nelas as dimensões da imagem, fazendo isso, depois criamos outra variável e atribuímos a ela uma matriz, utilizando a biblioteca numpy, neste código a matriz que foi utilizada foi uma matriz 5x5 de 1.

Agora podemos aplicar a erosão na imagem. Aplicamos a erosão na imagem para erodir os limites do objeto em primeiro plano. A erosão encolhe ou afina os objetos em uma imagem e também permite separar objetos nas imagens.
E a dilatação aumenta ou engrossa os objetos em uma imagem e também conecta objetos com proximidade menor que menor que o elemento estruturante. Faz a combinação da dilatação que expande, enquanto a erosão diminui os objetos da imagem. Essas funções geralmente são usadas em conjunto que daí gera a abertura e o fechamento.
A abertura é a erosão do objeto seguido da dilatação e o fechamento é a  dilatação do objeto seguido da erosão. Daí também pode se aplicar uma função que dá o contorno dos objetos que é a .morphologyEx() .
E finalizamos imprimindo as variáveis na tela com a função imshow().
