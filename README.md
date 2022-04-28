# Practica-4-Dibujo-sobre-una-imagen
Dibujo sobre una imagen creada con fondo negro

import numpy as np
import cv2 #Opencv

#img = cv2.imread('Pizarron.png', 1)
# Construcción de una imagen de 400x600 y RGB
Pizarra = 0 * np.ones((500, 500, 3),dtype=np.uint8)

# Linea (nombre_imagen,(a,b),(c,d),(B,G,R),Grosor)
# Desde (a,b) hasta (c,d), Donde (x,y)
cv2.line(Pizarra,(0,0),(500,500),(255,0,0),20)
cv2.line(Pizarra,(0,0),(500,500),(225,0,0),10)
cv2.line(Pizarra,(0,0),(500,500),(200,0,0),3)
cv2.line(Pizarra,(500,0),(0,500),(255,0,0),20)
cv2.line(Pizarra,(500,0),(0,500),(225,0,0),10)
cv2.line(Pizarra,(500,0),(0,500),(200,0,0),3)

# Rectangulo (nombre_imagen,(a,b),(c,d),(B,G,R),Grosor)
# Desde (a,b) hasta (c,d), Donde (x,y)
cv2.rectangle(Pizarra,(50,50),(450,450),(255,255,255),20)
cv2.rectangle(Pizarra,(50,50),(450,450),(225,225,225),10)
cv2.rectangle(Pizarra,(50,50),(450,450),(200,200,200),3)
# Circulo (nombre_imagen,(a,b),radio,(B,G,R),Grosor)
# Centro (a,b)
# Para rellenar el area es con un -1
cv2.circle(Pizarra,(250,250),140,(215,0,0),5)
cv2.circle(Pizarra,(250,250),135,(235,0,0),5)
cv2.circle(Pizarra,(250,250),130,(255,0,0),5)

cv2.circle(Pizarra,(250,250),125,(0,175,0),5)
cv2.circle(Pizarra,(250,250),120,(0,195,0),5)
cv2.circle(Pizarra,(250,250),115,(0,215,0),5)
cv2.circle(Pizarra,(250,250),110,(0,235,0),5)
cv2.circle(Pizarra,(250,250),105,(0,255,0),5)

cv2.circle(Pizarra,(250,250),100,(0,0,255),5)
cv2.circle(Pizarra,(250,250),100,(0,0,225),4)
cv2.circle(Pizarra,(250,250),100,(0,0,200),3)
cv2.circle(Pizarra,(250,250),100,(0,0,175),2)
cv2.circle(Pizarra,(250,250),100,(0,0,150),1)
cv2.circle(Pizarra,(250,250),100,(0,0,255),-1)

#Para texto
font = cv2.FONT_HERSHEY_SIMPLEX
# (nombre_imagen,texto,ubicación,fondo,tamaño_texto,color,grosor,tipo_de_linea)
cv2.putText(Pizarra,'LGT',(200,270),font,2,(0,255,0),2,cv2.LINE_AA)

# Convertir la imagen RGB a HSV, que es HSV??
hsv = cv2.cvtColor(Pizarra, cv2.COLOR_BGR2HSV)

# Definir intervalo del color para el Azul
azulbajo = np.array([215,0,0])
azulalto = np.array([255,0,0])

# Definir intervalo del color para el Verde
verdebajo = np.array([0,215,0])
verdealto = np.array([0,255,0])

# Definir intervalo del color para el Blanco
blancobajo = np.array([200,200,200])
blancoalto = np.array([255,255,255])

# Definir intervalo del color para el Rojo
rojobajo = np.array([0,0,255])
rojoalto = np.array([0,0,150])

# Umbralizar la imagen HSV para obtener solo los rango de colores
mask1 = cv2.inRange(hsv, verdebajo, verdealto)
mask2 = cv2.inRange(hsv, rojobajo, rojoalto)
mask3 = cv2.inRange(hsv, azulbajo, azulalto)
mask4 = cv2.inRange(hsv, blancobajo, blancoalto)

# Aislamiento por colores --------------------------------------- en proceso 

# Maneras de usar font
#cv2.putText(Pizarra,'LGT',(200,270),#fondo,2,(0,255,0),2,cv2.LINE_AA)
# El numero de fondo -> #fondo significa distintos tipos de letra
# 0 = cv2.FONT_HERSHEY_SIMPLEX
# 1 = cv2.FONT_HERSHEY_PLAIN
# 2 = cv2.FONT_HERSHEY_DUPLEX
# 3 = cv2.FONT_HERSHEY_COMPLEX
# 4 = cv2.FONT_HERSHEY_TRIPLEX
# 5 = cv2.FONT_HERSHEY_COMPLEX_SMALL
# 6 = cv2.FONT_HERSHEY_SCRIPT_SIMPLEX
# 7 = cv2.FONT_HERSHEY_SCRIPT_COMPLEX

cv2.imshow('Pizarra', Pizarra)
cv2.waitKey()
cv2.imshow('HSV', hsv)
cv2.waitKey()
cv2.imshow('Verde', mask1)
cv2.waitKey()
cv2.imshow('Rojo', mask2)
cv2.waitKey()
cv2.imshow('Azul', mask3)
cv2.waitKey()
cv2.imshow('Blanco', mask4)
cv2.waitKey()
cv2.destroyAllWindow()
