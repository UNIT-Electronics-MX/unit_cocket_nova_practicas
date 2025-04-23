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


.. figure:: /_static/schematic_block_1.png
    :align: center
    :alt: Diagrama pictorico
    :width: 50%

     Diagrama pictórico del contador binario

Modulación por ancho de pulso (PWM)
===================================

La modulación por ancho de pulso (PWM) es una técnica utilizada para controlar la cantidad de energía entregada a un dispositivo. En los microcontroladores, el PWM se utiliza para controlar la velocidad de los motores, el brillo de los LEDs y más.

.. warning:: 
    El soporte de ubicación para salidas PWM depende de la placa de desarrollo. Revisar la documentación de la placa para conocer los pines PWM disponibles.

.. only:: html

    .. figure:: /_static/cocket/pwm.gif
        :align: center
        :alt: figura-gif
        :width: 60%

Implementación
---------------


.. only:: html

    .. figure:: /_static/cocket/led.gif
        :align: center
        :alt: figura-gif
        :width: 60%


Arduino IDE y SDCC
~~~~~~~~~~~~~~~~~~



.. tabs::

     .. tab:: SDCC

          .. code-block:: c

                #include <stdio.h>
                #include "src/config.h"
                #include "src/system.h"
                #include "src/gpio.h"
                #include "src/delay.h"
                #include "src/pwm.h"

                #define MIN_COUNTER 10
                #define MAX_COUNTER 254
                #define STEP_SIZE   10

                void change_pwm(int hex_value)
                {
                     PWM_write(PIN_PWM, hex_value);
                }
                void main(void) 
                {
                     CLK_config();                          
                     DLY_ms(5);                            
                     PWM_set_freq(1);                    
                     PIN_output(PIN_PWM);       
                     PWM_start(PIN_PWM);      
                     PWM_write(PIN_PWM, 0);
                     while (1) 
                     {
                          for (int i = MIN_COUNTER; i < MAX_COUNTER; i+=STEP_SIZE) 
                          {
                                change_pwm(i);
                                DLY_ms(20);
                          }
                          for (int i = MAX_COUNTER; i > MIN_COUNTER; i-=STEP_SIZE)
                          {
                                change_pwm(i);
                                DLY_ms(20);
                          }
                     }
                }


     .. tab:: C++

          .. code-block:: cpp

               #define led 34

               int brightness = 0;
               int fadeAmount = 5;

               void setup() {
                    pinMode(led, OUTPUT);
               }

               void loop() {
                    analogWrite(led, brightness);
                    brightness = brightness + fadeAmount;
                    if (brightness <= 0 || brightness >= 255) {
                         fadeAmount = -fadeAmount;
                    }
                    delay(30);
               }

Aplicaciones
~~~~~~~~~~~~

Controlador de velocidad de motor