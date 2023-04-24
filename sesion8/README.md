# Manejo del puerto serial

### Funciones serial

API serial: https://www.arduino.cc/reference/en/language/functions/communication/serial/


Motor DC: 
* https://programarfacil.com/electronica/motor-dc/
* https://randomnerdtutorials.com/esp32-dc-motor-l298n-motor-driver-control-speed-direction/

|Función|Descripción|
|---|---|
|```Serial.begin()```|Configura la velocidad de transmisión serial (bits por segundo = baud).<br><br>**Sintaxis**:<br>```Serial.begin(speed)``` <br><br>**Parámetros**: <ul><li>**```speed```**: Velocidad de transmisión</ul>|
|```Serial.print()```|Imprime los datos del puerto serial en formato ASCII.<br><br>**Sintaxis**:<br>```Serial.print(val)```<br>```Serial.print(val, format)```<br><br>**Parámetros**: <ul><li>**```val```**: Valor a imprimir. El valor puede ser de cualquier tipo.<li>**```format```**: Formato de representación del ASCII (```DEC```, ```HEX```, ```OCT``` o ```BIN```).</ul>|
|```Serial.available()```|Obtiene el número de bytes (caracteres) disponibles por leer en el puerto serial. Estos son datos que ya han llegado y han sido almacenados en el buffer de recepción serial (el cual almacena 64 bytes).<br><br>**Sintaxis**:<br>```Serial.available()```<br><br>**Valores retornados**: Número de bytes disponibles para leer.|
|```Serial.read()```|Lee un dato que entra a través del serial.<br><br>**Sintaxis**:<br>```Serial.read()```<br><br>**Valores retornados**: Primer byte de los datos seriales disponibles (o ```-1``` si no hay datos disponibles). El tipo de dato leído es ```int```.|



Mejora: 
* https://serial-dashboard.github.io/index.html
* https://github.com/bjepson/Arduino-Cookbook-3ed-INO
* https://github.com/chillibasket/processing-grapher
* https://wired.chillibasket.com/processing-grapher/




https://arduinobot.pbworks.com/f/Manual+Programacion+Arduino.pdf

## Referencias

1. https://www.halvorsen.blog/documents/technology/iot/arduino.php
2. https://www.bogotobogo.com/index.php
3. https://developer.chrome.com/articles/usb/
4. https://learn.sparkfun.com/tutorials/connecting-arduino-to-processing/all
5. https://www.oreilly.com/library/view/arduino-cookbook/9781449399368/ch04.html
6. https://forum.arduino.cc/t/serial-input-basics-updated/382007
7. https://www.ladyada.net/learn/arduino/lesson4.html
8. https://deepbluembedded.com/esp32-hello-world-serial-print-arduino/
9. https://learn.adafruit.com/using-webusb-with-arduino-and-tinyusb/serial-communications-example
10. https://qxf2.com/blog/arduino-tutorials-for-testers-serial-monitor/
11. https://riptutorial.com/arduino/topic/1674/serial-communication
12. https://www.halvorsen.blog/documents/technology/iot/arduino/resources/Serial%20Communication%20between%20Arduino%20and%20LabVIEW.pdf
13. https://ww2.mathworks.cn/help/supportpkg/arduino/ref/send-and-receive-serial-data-using-arduino-hardware.html
14. https://startingelectronics.org/beginners/start-electronics-now/tut9-using-the-arduino-serial-port/
15. https://assiss.github.io/arduino-zhcn/cn/Tutorial/SoftwareSerialExample.html
16. https://arduinobot.pbworks.com/f/Manual+Programacion+Arduino.pdf
17. https://learn.sparkfun.com/tutorials/terminal-basics/all
18. https://learn.sparkfun.com/tutorials/serial-communication/wiring-and-hardware
18. https://learn.sparkfun.com/tutorials/serial-communication/res
19. https://learn.sparkfun.com/tutorials/serial-communication/uarts
20. https://learn.adafruit.com/circuit-playground-express-serial-communications/what-is-serial-communications
21. https://learn.sparkfun.com/tutorials/connecting-arduino-to-processing/to-processing
22. https://learn.sparkfun.com/tutorials/connecting-arduino-to-processing/to-processing
23. https://learn.sparkfun.com/tutorials/serial-basic-hookup-guide/all
24. https://learn.sparkfun.com/tutorials/serial-communication/all
25. https://learn.sparkfun.com/tutorials/terminal-basics/arduino-serial-monitor-windows-mac-linux
26. https://learn.adafruit.com/adafruit-arduino-lesson-5-the-serial-monitor/overview
27. https://www.bolanosdj.com.ar/MOVIL/ARDUINO2/ComuniSerialArduino.pdf
28. https://www.bolanosdj.com.ar/MOVIL/ARDUINO2/EjercicioDisplay7Continu.pdf
29. https://www.jgvaldemora.org/blog/tecnologia/wp-content/uploads/2016/10/PR%C3%81CTICAS-ARDUINO-20.pdf
30. https://www.paulrosero-montalvo.com/gallery/secap3.1.pdf
31. https://candy-ho.com/Drivers/librodeproyectosdearduinostarterkit-151212174250.pdf
32. https://idus.us.es/bitstream/handle/11441/101408/TFG-2873-PACHECO%20MARTINEZ.pdf?sequence=1&isAllowed=y
33. http://proyecto987.es/blog/wp-content/uploads/2016/04/Arduino-LabVIEW.pdf
34. https://repository.udistrital.edu.co/bitstream/handle/11349/13449/S%C3%A1nchezHuertasJulietteXimena2018.pdf?sequence=1&isAllowed=y
35. https://repository.unad.edu.co/bitstream/handle/10596/13295/1010023130.pdf?sequence=3&isAllowed=y
36. http://www.brunel.ac.uk/~emstaam/material/bit/Finite%20State%20Machine%20with%20Arduino%20Lab%203.pdf
37. https://upcommons.upc.edu/bitstream/handle/2117/87879/memoria.pdf?sequence=1&isAllowed=y
38. https://smartsys.web.unc.edu/wp-content/uploads/sites/16132/2018/09/lab2-thermistor-buzzer-serial-PWM.pdf
39. https://addi.ehu.es/bitstream/handle/10810/29158/TFG_BerthaLorenzoOchoa.pdf?se
40. https://ss-valpovo.hr/wp-content/uploads/2020/01/arduinoprojecthandbook.pdf
41. https://ecs-pw-facweb.ecs.csus.edu/~dahlquid/eee174/S2016/handouts/Labs/ArduinoLab/ArduinoInfo/
42. https://brown-cs1600.github.io/
