HID - Teclado
=========================

Introducción
------------
Este ejemplo demuestra la funcionalidad de un dispositivo HID configurado como teclado. Gracias al firmware keyboard.bin, el dispositivo simula la entrada de un teclado físico.

Firmware keyboard.bin
---------------------
El firmware keyboard.bin permite probar la funcionalidad de un teclado HID. Descárguelo y verifique el funcionamiento:

.. raw:: html

     <div style="text-align: right;">
          <br>
          <a href="https://github.com/UNIT-Electronics-MX/docs_cocket/releases/download/code_1/keyloop.bin" download="keyboard.bin">
               <button class="btn btn-primary" style="background-color: #007bff; border-color: #007bff; color: white; padding: 10px 20px; font-size: 16px; border-radius: 5px;">
                    Descargar firmware keyboard.bin
               </button>
          </a>
     </div>

.. figure:: /_static/pwm_motor/button.png
    :align: center
    :alt: figura-gif
    :width: 60%

    Aplicación de entrada digital
    
Visualización de la Interacción
-------------------------------
Observe el comportamiento del dispositivo a través de la siguiente animación:

.. only:: html

     .. figure:: /_static/usb/keyboard.gif
          :align: center
          :alt: Demostración del Teclado
          :width: 60%

Editor de Texto Simulado
-------------------------
Para complementar la prueba, use el editor de texto simulado y verifique la entrada de datos:

.. only:: html

     .. raw:: html

          <div style="text-align: center;">
                    <iframe src="_static/serial_console/notepad.html" width="660" height="500" style="border: none; margin: 0 auto;"></iframe>
          </div>

Referencias
-----------
- Documentación oficial USB: `USB Implementers Forum <https://www.usb.org/>`_
- Ejemplos de dispositivos HID en GitHub: `HID device examples <https://github.com/UNIT-Electronics/CH55x_SDCC_Examples>`_
