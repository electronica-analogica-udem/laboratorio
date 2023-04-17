# Aplicaciones del transistor BJT como switch

Circuito base:

![circuito_base](circuito_base.png)

$$i_B=\frac{v_I - V_{BE}}{R_B}$$

$$i_C=\beta i_B$$

$$v_C=V_{CC} - R_C i_C$$

## Led driver

Una aplicación bastante común de un transistor como switch es el **Driver para Leds**. En este, la carga es un led con su respectiva resistencia limitadora. 

![npn_switch](led_driver_npn1.png)

En el **driver para led**, el control del encendido y apagado del led dependerá de transistor. La siguiente figura muestra un circuito típico en el cual se ilustra este escenario:

![npn_switch](npn-switch-led.png)


**Ejemplo**: Supongamos que se quiere controlar el encendido y apagado de un led rojo a traves de un arduino. Calcule los valores de diseño para las resistencias necesarios para que a traves del led circule una corriente de $10 mA$

![arduino](arduino_led.png)

El led rojo tiene una caida de voltaje aproximadamente de $V_{Led}=1.8V$, el valor de $R_2$ lo podemos elegir a gusto, de modo que si asumimos que $R_2 = 100 \Omega$. El brillo del led depende de la corriente a traves de este y en el problema nos dijeron que este iba a ser de $10 mA$. Luego tenemos los siguientes datos para arrancar:
* $V_{Led} = 1.8 V$
* $I_C = I_{Led} = 10 mA$
* $R_B = R_1 = ?$

Para calcular $R_B = R_1$ se asume que el diodo se encuentra en estado de saturación de modo que podemos suponer para los calculos que:
* $V_{BE} = 0.7 V$
* $V_{CE(sat)} = 0.2 V$
* $V_{CE(EOS)} = V_{CE(sat)} = 0.2 V$
* $V_{I} = V_{control} = 5 V$

Del circuito tenemos que $I_{C}$ en saturación tenemos que:

$$I_{C} = I_{C(sat)} = \frac{V_{CC} - (V_{Led}+V_{CE(sat)})}{R_C}$$

Luego, reemplazando los valores conocidos tenemos:

$$10m=\frac{5-(1.8+0.2)}{R_C}$$

$$R_C=\frac{3}{10m}$$

$$R_C= R_2 = 300\Omega$$

Por otro lado, del datasheet ([link](https://www.onsemi.com/pdf/datasheet/p2n2222a-d.pdf)) del 2N2222, $\beta_{min} = 75$ para $10 mA$, de modo que:

$$I_B(EOS)=\frac{I_C(sat)}{\beta_{min}} = \frac{10m}{75} \approx 0.13\ mA$$

Luego $I_B$ se obtiene fijando un factor de saturación $FS$ mediante la expresión:

$$I_B = FS*I_{B(EOS)}$$

Asumiento $FS = 10$, tenemos que:

$$I_B = FS*I_{B(EOS)} = 10 * 0.13m = 1.3\ mA$$

Ademas al ser $I_B$:

$$I_B = \frac{v_I - V_{BE}}{R_B} = \frac{V_{control}-V_{BE}}{R_1}$$

Si reemplazamos los valores conocidos tenemos que:

$$1.3m = \frac{5 - 0.7}{R_1}$$

$$R_B = \frac{5 - 0.7}{1.3m}$$

$$R_B = R_1 = 2.54\ k\Omega$$

Finalmente, tendremos que:

$$\beta_F = \frac{I_C}{I_B} = \frac{10}{1.3} = 7.69 $$

Luego, si todo esta bien, se debe cumplir que $\beta_F \leq \beta_{min}$ lo cual es valido para el caso:

$$\beta_F \leq \beta_{min} \longrightarrow 7.69 \leq 75 $$

Finalmente los valores $R1$ y $R2$ de diseño son:

|Resistencia|Teorico|Comercial|
|---|---|---|
|$R_1$|$2.54\ k\Omega$|$2.7\ k\Omega$|
|$R_2$|$300\ \Omega$|$330\ \Omega$|

Como los valores de las resistencias dieron un poco diferentes respecto al valor original, es necesario realizar nuevamente los calculos teoricos de $I_B$ e $I_C$ para estos nuevos valores:

$$I_B = \frac{v_I - V_{BE}}{R_B} = \frac{V_{control}-V_{BE}}{R_1} = \frac{5-0.7}{2.7k} \approx 1.59\ mA  $$

$$I_{C} = \frac{V_{CC} - (V_{Led}+V_{CE(sat)})}{R_C} = \frac{5-(1.8-0.2)}{330} \approx 9.1\ mA$$

Luego para estos nuevos valores.

$$\beta_F = \frac{I_C}{I_B} = \frac{9.1}{1.59} = 5.72$$


### Simulación

Para modelar el led vamos a usar el modelo que se da en el siguiente [link](https://github.com/kicad-spice-library/KiCad-Spice-Library/blob/master/Models/Diode/led.lib). Si montamos la simulación en LTSpice, esta queda como se muestra a continuación:

![sim](spice_sim_led_driver.png)

Si graficamos las señales de interes:

![currents](currents.png)

![voltajes](voltajes.png)

De las graficas, podemos concluir lo siguiente:
* El transistor esta operando en corte y saturación tal y como se espera. 
  * **Transistor ON**: $V_I = 5V \longrightarrow V_C \approx 0V $
  * **Transistor OFF**: $V_I = 0V \longrightarrow V_C \approx 5V $
* Vemos que el valor para corriente en el colector, varia un poco mas respecto al calculo teorico, esto tal vez por el modelo empleado para el led:
  
   |Variable|Teorico|Simulado|
   |---|---|---|
   |$I_B$|$1.59\ mA$|$1.6\ mA$|
   |$I_C$|$9.1\ mA$|$15\ mA$|

Adicionalmente se muestra tambien la simulación en Tinkercad ([link](https://www.tinkercad.com/things/blcFVhwrI0F)) para ver el comportamiento con los valores calculados para las resistencias:

* **Transistor ON**:
  
  ![cerrado](cerrrado_tinkercad.png)

* **Transistor OFF**:
  
  ![abierto](abierto_tinkercad.png)

### Montaje real

Antes de realizar el montaje con el arduino, realizar el siguiente montaje con los valores calculados:

![montaje](montaje.png)

Como alimentación y tierra para el circuito, haga uso de los pineas **5V** y **GND** del arduino. Luego, empleando un multimetro realizar las siguientes mediciones y llenar las respectivas tablas:

* **Transistor ON**: $V_I = 5V$
  
  |Variable|Valor|
  |---|---|
  |$I_C$||
  |$I_B$||
  |$V_C$||
  |$V_{Led}$||

* **Transistor OFF**: $V_I = 0V$
  
  |Variable|Valor|
  |---|---|
  |$I_C$||
  |$I_B$||
  |$V_C$||
  |$V_{Led}$||

