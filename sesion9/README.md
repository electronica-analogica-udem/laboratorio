# Manejo del LCD

## Objetivos

> * Objetivo 1.
> * Objetivo 2.
> * Objetivo 3.

## Sobre los displays LCD



Liquid crystal displays (LCDs) and LED displays offer a convenient and inexpensive
way to provide a user interface for a project.



Son estremadamente utiles para el despliegue de mensajes (status mesaje) de los sistemas electronicos.


Diferentes tipos:
"standard" blue&white 16x2, RGB 16x2 LCDs, "standard" blue&white 20x4 and RGB 20x4.




Here is an example of a character LCD, 16 characters by 2 lines:

If you look closely you can see the little rectangles where the characters are displayed. Each rectangle is a grid of pixels. Compare this to a graphical LCD such as the following:


The graphical LCD has one big grid of pixels (in this case 128x64 of them) - It can display text but its best at displaying images. Graphical LCDs tend to be larger, more expensive, difficult to use and need many more pins because of the complexity added.




https://robosans.com/learn/embedded/arduino/16x2-lcd-interfacing-with-arduino/




https://naylampmechatronics.com/blog/34_tutorial-lcd-conectando-tu-arduino-a-un-lcd1602-y-lcd2004.html

-----

La siguiente figura muestra un LCD 16x2 con sus respectivos pines de interfaz:

![LCD_16x2](LCD_16x2.png)

La descripción de cada uno de los pines se muestra en la siguiente tabla (para mayor información puede consultar el manual de especificaciones: **Specifications Of LCD module** ([link](https://www.sparkfun.com/datasheets/LCD/ADM1602K-NSW-FBS-3.3v.pdf))).


|Pin|Simbolo|Función|
|---|---|---|
|1|**VSS**|Tierra (**GND**)|
|2|**VDD**|Alimentacion (**+5V**)|
|3|**V0**|Ajuste de contraste|
|4|**RS**|Señal de seleccion de registro de datos (**HIGH**) o instrucciones (**LOW**)|
|5|**RW**|Señal de seleccion para lectura (**HIGH**) o escritura (**LOW**)|
|6|**E**|Señal que habilita o deshabilita la escritura en el display|
|7-14|**D0-D7**|Bus de datos. Cuando la conexión entre el microcontrolador es usando ocho lineas, se emplean todos los pines; cuando la conexión es a cuatro lineas, solo se emplean los **D0-D3**|
|15|**A**|Alimentación positiva del backlight (**+5V**)|
|16|**K**|Alimentación negativa del backlight|**GND**|

Para mas información: https://openlabpro.com/guide/custom-character-lcd-pic/


LCD Commands:

There are some preset commands instructions in LCD, which we need to send to LCD through some microcontroller. Some important command instructions are given below (https://circuitdigest.com/sites/default/files/HD44780U.pdf):

|Hex Code|Command to LCD Instruction Register|
|---|---|
|```0F```|LCD ON, cursor ON|
|```01```|Clear display screen|
|```02```|Return home|
|```04```|Decrement cursor (shift cursor to left)|
|```06```|Increment cursor (shift cursor to right)|
|```05```|Shift display right|
|```07```|Shift display left|
|```0E```|Display ON, cursor blinking|
|```80```|Force cursor to beginning of first line|
|```C0```|Force cursor to beginning of second line|
|```38```|2 lines and 5×7 matrix|
|```83```|Cursor line 1 position 3|
|```3C```|Activate second line|
|```08```|Display OFF, cursor OFF|
|```C1```|Jump to second line, position 1|
|```OC```|Display ON, cursor OFF|
|```C1```|Jump to second line, position 1|
|```C2```|Jump to second line, position 2|

----

Las funciones se encuentran en la lubreria https://www.arduino.cc/reference/en/libraries/liquidcrystal/

Creates a variable of type LiquidCrystal. The display can be controlled using 4 or 8 data lines. If the former, omit the pin numbers for d0 to d3 and leave those lines unconnected. The RW pin can be tied to ground instead of connected to a pin on the Arduino; if so, omit it from this function’s parameters.

|Función|Descripción|
|---|---|
|```LiquidCrystal()```|Crea un objeto tipo ```LiquidCrystal``` para controlar el display. El display puede ser controlado usando usando una conexión a 4 (para lo cual se dejan sin conectar **D0-D3**) u 8 lineas. Adicionalmente, el pin **RW** lo cual permite que sea omitido como parametro de la función<br><br>**Sintaxis**:<br>```LiquidCrystal(rs, enable, d4, d5, d6, d7)``` <br>```LiquidCrystal(rs, rw, enable, d4, d5, d6, d7)```<br>```LiquidCrystal(rs, enable, d0, d1, d2, d3, d4, d5, d6, d7)```<br>```LiquidCrystal(rs, rw, enable, d0, d1, d2, d3, d4, d5, d6, d7)```<br><br>**Parámetros**: <ul><li>**```rs```**: Numero del pin del arduino conectado al pin **RS** del LCD<li>**```rw```**: Numero del pin del arduino conectado al pin **RW** del LCD<li>**```enable```**: Numero del pin del arduino conectado al pin **E** del LCD<li>**```d0, d1, d2, d3, d4, d5, d6, d7```**: Numero de los pines del arduino conectado a los correspondientes pines del bus de datos del LCD. Los parametros ```d0, d1, d2, d3``` son  opcionales y son omitidos cuando el LDC se conecta al arduino usando cuatro lineas</ul>|
|```lcd.begin()```|Especifica tipo de display que sera empleado indicando sus dimensiones (filas y columnas)<br><br>**Sintaxis**:<br>```lcd.begin(cols, rows)```<br><br>**Parámetros**: <ul><li>**```lcd```**: Variable tipo ```LiquidCrystal```.<li>**```cols```**: Numero de columnas que tiene el display.<li>**```rows```**: Numero de filas que tiene el display.</ul>|
|```lcd.clear()```|Borra la pantalla del LDC y coloca el cursor en la esquina superior izquierda.<br><br>**Sintaxis**:<br>```lcd.clear()```<br><br>**Parámetros**: <ul><li>**```lcd```**: Variable tipo ```LiquidCrystal```</ul>|
|```lcd.home()```|Posiciona el cursor en la parte superior izquierda de la pantalla LCD.<br><br>**Sintaxis**:<br>```lcd.home()```<br><br>**Parámetros**: <ul><li>**```lcd```**: Variable tipo ```LiquidCrystal```</ul>|
|```lcd.setCursor()```|Especifica la posición en la que se ubicara el cursor<br><br>**Sintaxis**:<br>```lcd.setCursor(col, row)```<br><br>**Parámetros**: <ul><li>**```lcd```**: Variable tipo ```LiquidCrystal```.<li>**```col```**: Columna en la que se ubicara el cursor (siendo 0 la primera columna).<li>**```row```**: Fila en la que se colocará el cursor (Donde 0 es la primera fila).</ul>|




----




https://circuitdigest.com/article/16x2-lcd-display-module-pinout-datasheet

https://www.axman.com/sites/default/files/HC-LCD%20Commands.pdf
https://www.philadelphia.edu.jo/academics/kaubaidy/uploads/ESD-lec12A.pdf

https://www.sparkfun.com/datasheets/LCD/GDM1602K.pdf



Simulador LCD ([link](https://people.ucalgary.ca/~smithmr/2015webs/encm511_15/15_Labs/SimulationForLab4/djlcdsim1/djlcdsim.html))


Generador de caracteres ([link](http://omerk.github.io/lcdchargen/)) varios ejemplos de uso en [Custom character generator LCD
](https://diyusthad.com/custom-character-generator-lcd)

https://www.quinapalus.com/hd44780udg.html




https://people.ucalgary.ca/~smithmr/2015webs/encm511_15/


https://www.uet.edu.pk/pp/ee/~mtahir/EE371/EE371/Experiment_9.pdf




que controla en qué parte de la memoria de la pantalla LCD está escribiendo datos. Puede seleccionar el registro de datos, que contiene lo que sucede en la pantalla, o un registro de instrucciones, que es donde el controlador de la pantalla LCD busca instrucciones sobre qué hacer a continuación.




. You can select either the data register, which holds what goes on the screen, or an instruction register, which is where the LCD's controller looks for instructions on what to do next.
A Read/Write (R/W) pin that selects reading mode or writing mode
An Enable pin that enables writing to the registers
8 data pins (D0 -D7). The states of these pins (high or low) are the bits that you're writing to a register when you write, or the values you're reading when you read.
There's also a display contrast pin (Vo), power supply pins (+5V and GND) and LED Backlight (Bklt+ and BKlt-) pins that you can use to power the LCD, control the display contrast, and turn on and off the LED backlight, respectively.

The process of controlling the display involves putting the data that form the image of what you want to display into the data registers, then putting instructions in the instruction register. The LiquidCrystal Library simplifies this for you so you don't need to know the low-level instructions.

The Hitachi-compatible LCDs can be controlled in two modes: 4-bit or 8-bit. The 4-bit mode requires seven I/O pins from the Arduino, while the 8-bit mode requires 11 pins. For displaying text on the screen, you can do most everything in 4-bit mode, so example shows how to control a 16x2 LCD in 4-bit mode.


Tomado de: https://naylampmechatronics.com/blog/34_tutorial-lcd-conectando-tu-arduino-a-un-lcd1602-y-lcd2004.html


Librería LiquidCrystal de Arduino
El IDE de Arduino ya viene con una librería que nos permite manejar diferentes tamaños de LCD’s, La documentación completa la pueden encontrar en la página oficial de Arduino: LiquidCrystal

Explicaremos las funciones principales, las cuales se usaran en este tutorial.

LiquidCrystal(rs, en, d4, d5, d6, d7)
Función constructor, crea una variable de la clase LiquidCrystal, con los pines indicados.

begin(cols, rows)
Inicializa el LCD, es necesario especificar el número de columnas (cols) y filas (rows) del LCD.

clear()
Borra la pantalla LCD y posiciona el cursor en la esquina superior izquierda (posición (0,0)).

setCursor(col, row)
Posiciona el cursor del LCD en la posición indicada por col y row (x,y); es decir, establecer la ubicación en la que se mostrará posteriormente texto escrito para la pantalla LCD.

write()
Escribir un carácter en la pantalla LCD, en la ubicación actual del cursor.

print()
Escribe un texto o mensaje en el LCD, su uso es similar a un Serial.print

scrollDisplayLeft()
Se desplaza el contenido de la pantalla (texto y el cursor) un espacio hacia la izquierda.

scrollDisplayRight()
Se desplaza el contenido de la pantalla (texto y el cursor) un espacio a la derecha.

createChar (num, datos)
Crea un carácter personalizado para su uso en la pantalla LCD. Se admiten hasta ocho caracteres de 5x8 píxeles (numeradas del 0 al 7). Donde: num es el número de carácter y datos es una matriz que contienen los pixeles del carácter. Se verá un ejemplo de esto mas adelante.

Explicado la librería veamos unos ejemplos:


-----


## Circuitos de interfaz

1. https://makeabilitylab.github.io/physcomp/arduino/
2. https://learn.adafruit.com/character-lcds
3. https://learn.sparkfun.com/tutorials/basic-character-lcd-hookup-guide/all
4. https://makeabilitylab.cs.washington.edu/
5. https://k12maker.mit.edu/physical-computing.html
6. https://www.instructables.com/member/EdgertonCenter/
7. https://guides.temple.edu/c.php?g=419841&p=2863656
8. https://wiki.ead.pucv.cl/Physical_Computing_-_UAI
9. https://arduinotogo.com/
10. https://github.com/arm-university/Smart-School-Projects
11. https://github.com/moritzsalla/phys-comp
12. https://www.ecarleton.ca/course/view.php?id=38
13. https://blogs.uw.edu/hcdepcom/projects/proj13/smart-home-arduino
14. http://oomlout.com/oom.php/index.htm
15. https://www.jodyculkin.com/category/pcomp

## Referencias

1. https://docs.arduino.cc/learn/electronics/lcd-displays
2. https://naylampmechatronics.com/blog/34_tutorial-lcd-conectando-tu-arduino-a-un-lcd1602-y-lcd2004.html
3. https://www.bolanosdj.com.ar/SOBRELCD/TEORIALCDV1.pdf
4. https://www.bolanosdj.com.ar/MOVIL/ARDUINO2/EjemploLCD.pdf
5. https://naylampmechatronics.com/blog/34_tutorial-lcd-conectando-tu-arduino-a-un-lcd1602-y-lcd2004.html
6. https://learn.sparkfun.com/tutorials/basic-character-lcd-hookup-guide/all
7. https://www.quinapalus.com/hd44780udg.html
8. https://randomnerdtutorials.com/esp32-esp8266-i2c-lcd-arduino-ide/
9. http://www.dinceraydin.com/djlcdsim/djlcdsim.html
10. https://www.adafruit.com/product/181
11. https://learn.adafruit.com/character-lcds
12. https://learn.adafruit.com/light-meter
13. https://wiki.seeedstudio.com/Grove-16x2_LCD_Series/
14. https://makeabilitylab.github.io/physcomp/arduino/
15. https://users.cs.utah.edu/~elb/Papers/PhysicalComputingTalk.pdf
16. https://pdm.lsupathways.org/4_physicalcomputing/
17. https://www.uet.edu.pk/pp/ee/~mtahir/EE371/EE371_Fall2014.html
    