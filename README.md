# boton-y-ChatGTP


# -*- coding: utf-8 -*-
"""
Created on Sun Apr 30 22:28:40 2023

@author: Andres Gutierrez
"""

from machine import Pin, I2C
from time import sleep_ms
from ssd1306 import SSD1306_I2C #libreria del oled
import framebuf


ANCHO = 128
ALTO = 64
MODO_MAX = 5
global modo
global contador
modo = 0
contador = 0

boton = Pin(16,Pin.IN, Pin.PULL_DOWN)
i2c = I2C(1,scl = Pin(19), sda = Pin(18)) #los pines en los que mandara la informacion del oled
oled = SSD1306_I2C(ANCHO, ALTO, i2c) #

def boton_interrumpir(pin)
    global modo
    global contador
    
    if boton.value():
        modo += 1
        print(modo)
        
    if modo > MODO_MAX:
        modo = 0
        contador = 0
        
boton.irq(trigger =Pin.IRQ_RISSING, hadler= boton_interrumpir)


while True:
    oled.fill(0)
    
    if modo == 0:
        oled.text("Toma agua ",0,0)
        oled.text("Hora : 7 AM",0,10)
        oled.text("Primer baso",0,20)
        oled.text("Matutino",0,30)

        
    if modo == 1:
        oled.text("Toma agua",0,0)
        oled.text("Hola : 9 AM",0,10)
        oled.text("Segundo baso",0,20)
        oled.text("Matutino",0,30)
        
    if modo == 2:
        oled.text("Toma agua",0,0)
        oled.text("Hora : 11 AM",0,10)
        oled.text("tercer baso",0,20)
        oled.text("vespertino",0,30)
        
    if modo == 3:
        oled.text("Toma agua",0,0)
        oled.text("Hora : 1 PM",0,10)
        oled.text("Cuarto baso",0,20) 
        oled.text("vespertino",0,30)
        
    if modo == 4:
        oled.text("Toma agua",0,0)
        oled.text("Hora : 4 PM",0,10)
        oled.text("quinto baso",0,30)
        oled.text("vespertino",0,40)
        
     if modo == 5:
        oled.text("Toma agua",0,0)
        oled.text("Hora : 7 PM",0,30)
        
     oled.show()
