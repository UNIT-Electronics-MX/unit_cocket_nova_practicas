Grabar Firmware
===============




Cocket Nova CH552G Usando WCHISPTool (Windows OS)
------------------------------------------------
Este tutorial ofrece un método sencillo para actualizar el firmware en el Cocket Nova CH552G utilizando WCHISPTool. Este enfoque garantiza que tu placa esté operativa rápidamente, independientemente de si utilizas archivos .bin o .hex (generados usando el compilador SDCC).

Paso 1: Abre WCHISPTool e instala los drivers necesarios.
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^


1. Para garantizar que tu PC y el dispositivo se comuniquen correctamente, instala el driver USB CH372.

2. Inicia WCHISPTool: abre el programa en tu computadora.

3. Conecta tu dispositivo: coloca el CH552G en Modo de Arranque manteniendo presionado el botón de arranque mientras lo conectas a tu PC mediante USB.

.. note::
     
    WCHISPTool detectará automáticamente tu dispositivo y configurará los ajustes apropiados para el chip CH552G. No necesitas seleccionar el chip manualmente.



.. figure:: /_static/carga/chip.png
   :align: center
   :alt: OLED a Cocket Nova
   :width: 60%
   
   OLED a Cocket Nova



Paso 2: Carga el archivo de firmware
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

1. Navega a la sección "Archivo de Descarga" en WCHISPTool.


.. figure:: /_static/carga/path.png
   :align: center
   :alt: OLED a Cocket Nova
   :width: 60%
   
    Ruta del firmware



2. Haz clic en el ícono de "Archivo Objeto" y localiza tu archivo de firmware.
    Formatos soportados: .bin o .hex (generados usando el compilador SDCC).


3. Selecciona el archivo y asegúrate de que la casilla de "Archivo de Descarga" esté activada.

.. figure:: /_static/carga/path_l.png
   :align: center
   :alt: OLED a Cocket Nova
   :width: 60%
   
    Selección del firmware
   

Paso 3: Graba el firmware
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

1. Confirma que el dispositivo esté en Modo de Arranque.

2. Haz clic en el botón "Descargar" para iniciar el grabado del firmware.

3. Una barra de progreso indicará el estado. Espera a que el proceso se complete.

.. figure:: /_static/carga/load.png
   :align: center
   :alt: OLED a Cocket Nova
   :width: 60%
   
    Proceso de grabado


.. tip::

    Para un proceso más simplificado, la opción de Descarga Automática de WCHISPTool lo simplifica todo:
    
    - El programa detecta automáticamente el dispositivo conectado, carga el firmware y maneja el proceso de grabado sin requerir intervención manual.

Con estos pasos, tu Cocket Nova CH552G se habrá grabado exitosamente y estará listo para el desarrollo.



Loadupch (GNU/Linux OS)
-----------------------
