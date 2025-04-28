Salidas Digitales
=================

Las salidas digitales facilitan la interacción con dispositivos externos. En los microcontroladores, se emplean para activar o desactivar LEDs, controlar relés, gestionar motores, entre otras aplicaciones.

.. tip::
     Open-drain y Open-collector

     Algunos microcontroladores incluyen salidas de drenaje abierto (open-drain) o de colector abierto (open-collector). Estas configuraciones son ideales para manejar dispositivos con alta demanda de corriente o para establecer comunicaciones bidireccionales.

     - **Open-drain**: Permite conectar la salida a tierra (GND), pero no a VCC.
     - **Open-collector**: Permite conectar la salida a VCC, pero no a tierra (GND).

Parpadeo de LED (Blink)
-----------------------

El parpadeo de un LED es un proyecto clásico en la introducción a los microcontroladores. Aunque el código varíe entre Arduino IDE y SDCC, el objetivo principal es lograr un efecto de parpadeo en el LED.


.. tip:: 

     En la tarjeta de desarrollo Cocket Nova, el LED integrado está conectado al pin 34. Para encenderlo, se debe configurar el pin como salida y luego alternar su estado entre alto (HIGH) y bajo (LOW).

.. _figura-LED:

.. figure::  /_static/cocket/led.jpg
    :align: center
    :alt: LEDs
    :width: 30%

    LED integrado
 
Arduino IDE y SDCC 
~~~~~~~~~~~~~~~~~~

.. _figura_output_led:

.. figure::  /_static/cocket/ouput_led.png
    :align: center
    :alt: LEDs
    :width: 60%

    LEDs

.. tabs::


     .. tab:: SDCC

          .. code-block:: c

                #include "src/system.h" 
                #include "src/gpio.h"  
                #include "src/delay.h"  

                #define PIN_LED P34

                void main(void)
                {
                    CLK_config();
                    DLY_ms(5);

                    PIN_output(PIN_LED);
                    while (1)
                    {
                         PIN_toggle(PIN_LED);
                         DLY_ms(500);
                    }
                }

     .. tab:: C++

          .. code-block:: cpp

                #define LED_BUILTIN 34

                void setup() {
                    pinMode(LED_BUILTIN, OUTPUT);
                }

                void loop() {
                    digitalWrite(LED_BUILTIN, HIGH); 
                    delay(500);
                    digitalWrite(LED_BUILTIN, LOW);    
                    delay(500);
                }

     


Aplicaciones
~~~~~~~~~~~~
Contador binarios 3 bits



.. figure:: /_static/cocket/semaforo.jpg
    :align: center
    :alt: contador binario
    :width: 50%

    Semáforo (ejemplo de contador binario)

.. list-table:: LED Connections
     :header-rows: 1

     * - Pin
       - Description
     * - GND
       - Común
     * - R
       - led rojo
     * - Y
       - led amarillo
     * - G
       - led verde

.. raw:: html

    <div style="text-align: right;">
      <br>
      <a href="https://github.com/UNIT-Electronics-MX/docs_cocket/releases/download/code_1/counter.bin" download="counter.bin">
         <button class="btn btn-primary" style="background-color: #007bff; border-color: #007bff; color: white; padding: 10px 20px; font-size: 16px; border-radius: 5px;">
            Firmware counter.bin
         </button>
      </a>
    </div>

.. figure:: /_static/pwm_motor/counter.png
    :align: center
    :alt: Diagrama pictorico
    :width: 50%

     Diagrama pictórico del contador binario


.. only:: html

   .. raw:: html
      
      <iframe src="_static/serial_console/serial_console.html" width="100%" height="500" style="border:none;"></iframe>
      <br>
      
