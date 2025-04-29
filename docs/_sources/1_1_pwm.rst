
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
.. raw:: html

   <div style="text-align: right;">
     <br>
     <a href="https://github.com/UNIT-Electronics-MX/docs_cocket/releases/download/code_1/servo.bin" download="servo.bin">
       <button class="btn btn-primary" style="background-color: #007bff; border-color: #007bff; color: white; padding: 10px 20px; font-size: 16px; border-radius: 5px;">
         Firmware servo.bin
       </button>
     </a>
   </div>

Controlador de servomotor

.. figure:: /_static/pwm_motor/servo.png
    :align: center
    :alt: servomotor
    :width: 60%

    Controlador de servomotor