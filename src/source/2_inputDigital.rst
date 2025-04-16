Entradas digitales
==================

Las entradas digitales son una forma de interactuar con el mundo exterior. En la mayoría de los microcontroladores, las entradas digitales se utilizan para leer el estado de un botón, un sensor digital, un interruptor y más.

Pull-up y Pull-down
-------------------

La mayoría de los microcontroladores tienen resistencias pull-up y pull-down internas. Estas resistencias se utilizan para mantener un valor lógico alto o bajo en una entrada digital cuando no se aplica una señal externa.

- **Pull-up**: La resistencia pull-up conecta la entrada a VCC (nivel alto).
- **Pull-down**: La resistencia pull-down conecta la entrada a tierra (nivel bajo).

Estas resistencias pueden activarse o desactivarse mediante software. En algunos microcontroladores, como el CH552, las resistencias pull-up y pull-down se pueden configurar con un valor de resistencia específico. 

También es posible utilizar resistencias externas para pull-up y pull-down. Esto es útil cuando se necesita un valor de resistencia específico o cuando las resistencias internas no son suficientes.


Lectura de Entradas
-------------------

La lectura de una entrada digital en un microcontrolador es un proceso sencillo. La entrada puede estar en uno de dos estados: alto (HIGH) o bajo (LOW). En la mayoría de los microcontroladores, el estado alto corresponde a un valor lógico de 1 y el estado bajo a un valor lógico de 0.



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
            