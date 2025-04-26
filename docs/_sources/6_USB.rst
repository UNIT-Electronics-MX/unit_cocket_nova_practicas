Interfaz USB
============

Introducción
------------
La interfaz USB es un estándar de comunicación ampliamente utilizado para la conexión y alimentación de dispositivos. En el contexto de microcontroladores, se utiliza para realizar tareas como la transferencia de datos, actualización de firmware, depuración, entre otras.

Protocolos y Modo de Operación
------------------------------
Existen diferentes protocolos USB según la aplicación. Algunos de los más usados en microcontroladores son:

- HID (Dispositivo de Interfaz Humano): Para la interacción directa con el usuario mediante dispositivos como teclados y ratones.
- CDC (Dispositivo de Comunicación de Datos): Para establecer puertos seriales virtuales.
- MSC (Dispositivo de Clase Masiva): Para el intercambio de archivos con dispositivos de almacenamiento.

Interfaz HID (Dispositivo de Interfaz Humano)
---------------------------------------------

HID (Human Interface Device) permite a los dispositivos electrónicos interactuar con un usuario. Entre los dispositivos HID se incluyen teclados, ratones, joysticks, y gamepads.

.. figure:: /_static/cocket/hid_example.png
    :align: center
    :alt: HID
    :width: 60%

    Ejemplo de Dispositivo HID

.. raw:: html

     <table style="width: 100%; border-collapse: collapse; border: 1px solid #ccc;">
     <tr>
          <th style="border: 1px solid #ccc; padding: 8px;">Biblioteca</th>
          <th style="border: 1px solid #ccc; padding: 8px;">Enlace</th>
     </tr>
     <tr>
          <td style="border: 1px solid #ccc; padding: 8px;">HID Teclado y Ratón</td>
          <td style="border: 1px solid #ccc; padding: 8px;"><a href="https://github.com/UNIT-Electronics/CH55x_SDCC_Examples/tree/main/Software/examples/USB/USB-HID" target="_blank">HID device</a></td>
     </tr>
    </table>

Ejemplo de Firmware para HID (Mouse)
-------------------------------------
El firmware mouse.bin permite probar la funcionalidad de un dispositivo HID en forma de mouse. Para la descarga, utiliza el siguiente botón:

.. raw:: html

    <div style="text-align: right;">
      <br>
      <a href="_mouse.bin" download="mouse.bin">
         <button class="btn btn-primary" style="background-color: #007bff; border-color: #007bff; color: white; padding: 10px 20px; font-size: 16px; border-radius: 5px;">
            Firmware mouse.bin
         </button>
      </a>
    </div>

Prueba de HID
~~~~~~~~~~~~~~~~~~~

Para interactuar con el dispositivo HID, carga el firmware en el microcontrolador y utiliza el navegador para observar las reacciones. El siguiente GIF muestra una secuencia de prueba:

.. only:: html

     .. figure:: /_static/usb/cursor.gif
          :align: center
          :alt: figura-gif
          :width: 60%

Adicionalmente, se incluye una demostración interactiva:

.. only:: html

     .. raw:: html

          <div style="text-align: center;">
                <iframe src="_static/processing/cube.html" width="660" height="400" style="border: none; margin: 0 auto;"></iframe>
          </div>

Interfaz HID (Teclado)
~~~~~~~~~~~~~~~~~~~~~~~

El firmware keyboard.bin permite probar la funcionalidad de un dispositivo HID en forma de teclado.

.. raw:: html

    <div style="text-align: right;">
      <br>
      <a href="_keyboard.bin" download="keyboard.bin">
         <button class="btn btn-primary" style="background-color: #007bff; border-color: #007bff; color: white; padding: 10px 20px; font-size: 16px; border-radius: 5px;">
            Firmware keyboard.bin
         </button>
      </a>
    </div>

Visualización de la Interacción del Teclado
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. only:: html

     .. figure:: /_static/usb/keyboard.gif
          :align: center
          :alt: figura-gif
          :width: 60%

Otra de las pruebas se puede realizar accediendo a un editor de texto simulado:

.. only:: html

     .. raw:: html

          <div style="text-align: center;">
                <iframe src="_static/serial_console/notepad.html" width="660" height="500" style="border: none; margin: 0 auto;"></iframe>
          </div>



Referencias
-----------

- Documentación oficial de USB: `USB Implementers Forum <https://www.usb.org/>`_
- Ejemplos de firmware HID en GitHub: `HID device examples <https://github.com/UNIT-Electronics/CH55x_SDCC_Examples>`_

Con este complemento se busca ofrecer una visión más amplia y detallada de la interfaz USB y sus aplicaciones en dispositivos con microcontroladores.
