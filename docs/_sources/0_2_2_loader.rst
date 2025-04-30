Grabar Firmware
===============

Cocket Nova CH552G Usando WCHISPTool (Windows OS)
--------------------------------------------------
Este tutorial ofrece un método sencillo para actualizar el firmware en el Cocket Nova CH552G utilizando WCHISPTool. Este enfoque garantiza que tu placa esté operativa rápidamente, independientemente de si utilizas archivos .bin o .hex (generados usando el compilador SDCC).

Paso 1: Abre WCHISPTool e instala los controladores necesarios.
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

1. Para garantizar que tu PC y el dispositivo se comuniquen correctamente, instala el `driver USB CH372. <https://www.wch-ic.com/downloads/CH372DRV_EXE.html>`_

2. Inicia WCHISPTool: abre el programa en tu computadora.

3. Conecta tu dispositivo: coloca el CH552G en modo boot presionando el botón de boot mientras lo conectas a tu PC mediante USB.

.. note::

    WCHISPTool detectará automáticamente tu dispositivo y configurará los ajustes apropiados para el chip CH552G. No necesitas seleccionar el chip manualmente.

.. figure:: /_static/carga/chip.png
    :align: center
    :alt: OLED a Cocket Nova
    :width: 60%
    
    OLED a Cocket Nova

Paso 2: Carga el archivo de firmware
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

1. Navega a la sección "Archivo de Descarga" en WCHISPTool.

.. figure:: /_static/carga/path.png
    :align: center
    :alt: Ruta del firmware
    :width: 60%
    
    Ruta del firmware

2. Haz clic en el ícono de "Archivo Objeto" y localiza tu archivo de firmware.
    Formatos soportados: .bin o .hex (generados usando el compilador SDCC).

3. Selecciona el archivo y asegúrate de que la casilla de "Archivo de Descarga" esté activada.

.. figure:: /_static/carga/path_l.png
    :align: center
    :alt: Selección del firmware
    :width: 60%
    
    Selección del firmware

Paso 3: Graba el firmware
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

1. Confirma que el dispositivo esté en Modo de Arranque.

2. Haz clic en el botón "Descargar" para iniciar el grabado del firmware.

3. Una barra de progreso indicará el estado. Espera a que el proceso se complete.

.. figure:: /_static/carga/load.png
    :align: center
    :alt: Proceso de grabado
    :width: 60%
    
    Proceso de grabado

.. tip::

     Para un proceso más simplificado, la opción de Descarga Automática de WCHISPTool lo simplifica todo:
     
     - El programa detecta automáticamente el dispositivo conectado, carga el firmware y gestiona el proceso de grabado sin requerir intervención manual.

Con estos pasos, tu Cocket Nova CH552G se habrá grabado exitosamente y estará listo para el desarrollo.


Loadupch (GNU/Linux OS)
------------------------

Basado en el trabajado chprog la cual es una herramienta en Python para flashear fácilmente microcontroladores de la serie CH55x con versiones de bootloader 1.x y 2.x.x.


.. list-table:: Información del Proyecto
    :widths: 20 80
    :header-rows: 1

    * - Campo
      - Valor
    * - Proyecto
      - chprog - Herramienta de Programación para Microcontroladores CH55x
    * - Versión
      - v1.2 (2022)
    * - Créditos
      - Stefan Wagner
    * - GitHub
      - `wagiminator <https://github.com/wagiminator>`_
    * - Licencia
      - MIT License


**Referencias:**  

Inspirado y basado en chflasher y wchprog de Aaron Christophel y Julius Wang:

- `ATCnetz <https://ATCnetz.de>`_
- `chflasher en GitHub <https://github.com/atc1441/chflasher>`_
- `wchprog en GitHub <https://github.com/juliuswwj/wchprog>`_

Una vez compilado el proyecto, debes flashear el programa en el dispositivo CH55x. Sigue estos pasos:

1. **Conecta el Dispositivo**

- Asegúrate de que tu dispositivo CH55x esté conectado y que el botón BOOT esté presionado, tal como se indicó en el paso de compilación.

2. **Flashea el Programa**

- Ejecuta el siguiente comando para flashear el programa compilado en el microcontrolador:

.. code-block:: bash

    python ../../tools/chprog.py  main.bin

.. figure:: /_static/compile/led.png
    :width: 80%
    :align: center
    :alt: Efecto de parpadeo del LED

    Efecto de parpadeo del LED

.. note::

    Requiere que el controlador `libusb-win32` esté instalado usando Zadig.

Loadupch
~~~~~~~~

El `Loadupch <https://pypi.org/project/loadupch/>`_ es un oriyecto de desarrollo de software diseñado para facilitar la carga de código al microcontrolador CH552 con interfaz grafica. Es una herramienta amigable que proporciona una interfaz gráfica, facilitando a los usuarios la tarea de subir su código. Basada en chprog, Loadupch es una herramienta en Python que simplifica el proceso de flasheo de microcontroladores de la serie CH55x con versiones de bootloader 1.x y 2.x.x.

.. caution:: 

    Soporte disponible solo para GNU/Linux.


.. figure:: /_static/compile/loadupch.png
    :width: 50%
    :align: center
    :alt: Interfaz de la herramienta Loadupch

    Interfaz de la herramienta Loadupch

Instalando Loadupch
~~~~~~~~~~~~~~~~~~~~

.. warning::

    La herramienta Loadupch se encuentra actualmente en desarrollo y puede contener errores. Utilízala bajo tu propio riesgo.

Para instalar la herramienta Loadupch, puedes usar `pypi`. Sigue estos pasos:

1. **Instala Loadupch**

- Utiliza el siguiente comando para instalar la herramienta `Loadupch <https://github.com/UNIT-Electronics/ue_loadupch_Loader_Firmware->`_ mediante pip:

.. code-block:: bash

    pip install loadupch

2. **Ejecuta Loadupch**

- Después de la instalación, puedes ejecutar la herramienta Loadupch con el siguiente comando:

.. code-block:: bash

    python -m loadupch

.. caution::

    Requiere de asignación de permisos para acceder al dispositivo USB. 


Esto lanzará la interfaz gráfica de la herramienta Loadupch, permitiéndote cargar código al microcontrolador CH552 de manera sencilla.

.. tip::

    Si necesitas desinstalar la herramienta Loadupch por cualquier motivo, utiliza el siguiente comando:

    .. code-block:: bash

        pip uninstall loadupch

.. note::

    Requiere que el controlador `libusb-win32` esté instalado usando Zadig.
