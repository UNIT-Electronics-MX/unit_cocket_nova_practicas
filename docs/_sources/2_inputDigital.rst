Entradas Digitales
==================

Las entradas digitales permiten la interacción directa entre el microcontrolador y el entorno. Se emplean habitualmente para monitorear el estado de botones, sensores y otros dispositivos digitales.

Resistencias Internas Pull-up y Pull-down
-----------------------------------------

La mayoría de los microcontroladores incluyen resistencias internas pull-up y pull-down que aseguran un nivel lógico definido cuando no se aplica una señal externa:

- **Pull-up**: Conecta la entrada a VCC, garantizando un nivel lógico alto.
- **Pull-down**: Conecta la entrada a tierra, asegurando un nivel lógico bajo.

Estas resistencias pueden habilitarse o deshabilitarse mediante software. Por ejemplo, en el microcontrolador CH552 se puede configurar una resistencia interna con un valor específico, adaptándose a los requerimientos del diseño.

Asimismo, es posible utilizar resistencias externas para obtener un valor de resistencia determinado o cuando las resistencias internas no son suficientes.

Lectura de Entradas
-------------------

El proceso de lectura de una entrada digital es sencillo. El estado de la entrada se limita a dos valores posibles: alto (HIGH) y bajo (LOW), que corresponden a los niveles lógicos 1 y 0 respectivamente.


.. only:: html

    .. figure:: /_static/cocket/input.gif
        :align: center
        :alt: figura-gif
        :width: 60%


Arduino IDE y SDCC
-------------------


.. tabs::
               
    .. tab:: C++

        .. code-block:: cpp

            #include <Serial.h>

            void setup() {
            // No need to init USBSerial
            pinMode(33, INPUT);
            pinMode(34, OUTPUT);
            }

            void loop() {
            // Leer el valor del botón en una variable
            int sensorVal = digitalRead(11);
            // Imprimir el valor del botón en el monitor serial
            USBSerial_println(sensorVal);
            if (sensorVal == HIGH) {
                digitalWrite(33, LOW);
            } else {
                digitalWrite(33, HIGH);
            }

            delay(10);
            }

    .. tab:: SDCC

        .. code-block:: c

            #include "src/system.h" 
            #include "src/gpio.h"   
            #include "src/delay.h"  

            #define PIN_LED P34
            #define PIN_BUTTON P33

            void main(void)
            {
            CLK_config();
            DLY_ms(5);
            PIN_input(PIN_BUTTON);
            PIN_output(PIN_LED);
            while (1)
            {
                if (PIN_read(PIN_BUTTON)){
                PIN_high(PIN_LED);
                }
                else{
                PIN_low(PIN_LED);
                }
            }
            }

Aplicaciones
-------------

.. figure:: /_static/pwm_motor/button.png
    :align: center
    :alt: figura-gif
    :width: 60%

    Aplicación de entrada digital