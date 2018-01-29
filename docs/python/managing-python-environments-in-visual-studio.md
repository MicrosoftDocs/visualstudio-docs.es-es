---
title: "Administración de entornos de Python en Visual Studio | Microsoft Docs"
description: "Describe cómo usar la ventana Entornos de Python en Visual Studio para administrar entornos globales y virtuales, configurar entornos personalizados, instalar intérpretes de Python, instalar paquetes, establecer rutas de búsqueda y administrar entornos para proyectos de Visual Studio."
ms.custom: 
ms.date: 01/16/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: 
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 146e3f80de674e6219d1f7c89ea4186b66ee310f
ms.sourcegitcommit: bd16e764134c436d2d2f46490f51234d5246ee50
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/22/2018
---
# <a name="python-environments"></a>Entornos de Python

Un *entorno* de Python es un contexto en el que se ejecuta código de Python. Un entorno consta de un intérprete, una biblioteca (normalmente la biblioteca estándar de Python) y un conjunto de paquetes instalados. Todos estos componentes determinan qué construcciones de lenguaje y sintaxis son válidas, a qué función de sistema operativo puede acceder y qué paquetes puede usar.

En Visual Studio, todos los entornos se administran con la [ventana Entornos de Python](#managing-python-environments-in-visual-studio), tal y como se describe en este artículo. En cualquier proyecto dado, se selecciona un entorno para utilizarlo con el objeto de ejecutar el código, depurar, comprobar la sintaxis, mostrar la finalización de las importaciones y los miembros y cualquier otra tarea que sea específica del intérprete y las bibliotecas instaladas. Visual Studio también mantiene una base de datos de IntelliSense para cada entorno que proporciona finalización automática al escribir código.

Visual Studio proporciona además compatibilidad para entornos virtuales, archivos `requirements.txt` y rutas de acceso de búsqueda.

**Nota**: Si no está familiarizado con Python en Visual Studio, vea los siguientes artículos para obtener los conocimientos necesarios:

- [Uso de Python en Visual Studio](overview-of-python-tools-for-visual-studio.md)
- [Instalación de la compatibilidad con Python en Visual Studio](installing-python-support-in-visual-studio.md)

## <a name="global-and-virtual-environments"></a>Entornos globales y virtuales

Hay dos tipos de entornos de Python: globales y virtuales.

**Entornos globales**: cada instalación de Python (por ejemplo, Python 2.7, Python 3.6 y Anaconda 4.4.0 (consulte [Selección e instalación de los intérpretes de Python](#selecting-and-installing-python-interpreters)) mantiene su propio entorno. Cada entorno está formado por el intérprete de Python determinado, su biblioteca estándar y un conjunto de paquetes instalados previamente. Al instalar un paquete en un entorno global, este pasa a estar disponible para todos los proyectos que usan ese entorno. Si el entorno está ubicado en una área protegida del sistema de archivos (dentro de `c:\program files`, por ejemplo), la instalación de paquetes requiere privilegios de administrador.

Los entornos globales están disponibles para todos los proyectos del equipo. En Visual Studio, debe seleccionar un entorno global como predeterminado, que será el que se utilice para todos los proyectos (a menos que elija específicamente otro diferente para un proyecto). Para obtener más información, consulte [Selección de un entorno para un proyecto](#selecting-an-environment-for-a-project).

**Entornos virtuales**: debido a que los paquetes instalados en un entorno global están disponibles para todos los proyectos que lo usan, puede haber conflictos cuando dos proyectos requieren paquetes incompatibles o versiones diferentes del mismo paquete. Los entornos virtuales evitan estos conflictos utilizando el intérprete y la biblioteca estándar de un entorno global pero manteniendo sus propios almacenes de paquetes en carpetas aisladas.

En Visual Studio, puede crear un entorno virtual para un proyecto específico, que se almacena en una subcarpeta en el proyecto (vea [Creating virtual environments](#creating-virtual-environments) (Creación de entornos virtuales). El archivo del proyecto también identifica el entorno virtual. Visual Studio también registra todos los paquetes que instale en ese entorno virtual en el archivo `requirements.txt` del proyecto. Si luego comparte el proyecto y otros desarrolladores lo abren en sus equipo, Visual Studio ofrece la opción de volver a crear el entorno virtual.

### <a name="selecting-and-installing-python-interpreters"></a>Selección e instalación de los intérpretes de Python

De forma predeterminada, la instalación de la carga de trabajo de desarrollo de Python en Visual Studio de 2017 también instala Python 3 (64 bits). Puede optar por instalar las versiones de 32 bits y 64 bits de Python 2, Python 3, Anaconda 2 y Anaconda 3, como se describe en [Instalación](installing-python-support-in-visual-studio.md). También puede instalar manualmente cualquiera de los intérpretes que aparece en la tabla siguiente.

Para Visual Studio 2015 y versiones anteriores, debe instalar manualmente uno de los intérpretes.

Visual Studio (todas las versiones) crea automáticamente un entorno para cada intérprete de Python instalado mediante la comprobación del Registro (siguiendo [PEP 514: registro de Python en el Registro de Windows](https://www.python.org/dev/peps/pep-0514/)). Si Visual Studio no detecta un entorno instalado, consulte la sección [Creación de un entorno para un intérprete existente](#creating-an-environment-for-an-existing-interpreter).

| Intérprete | Description |
| --- | --- |
| [CPython](https://www.python.org/) | Intérprete "nativo" y que se usa con más frecuencia, disponible en versiones de 32 y 64 bits (se recomienda la versión de 32 bits). Incluye características más recientes del lenguaje, máxima compatibilidad con paquetes de Python, compatibilidad completa con la depuración e interoperabilidad con [IPython](http://ipython.org/). Consulte también: [Should I use Python 2 or Python 3? (¿Debo usar Python 2 o Python 3?)](http://wiki.python.org/moin/Python2orPython3). Tenga en cuenta que Visual Studio 2015 y las versiones anteriores no admiten Python 3.6 y pueden generar el error de no compatibilidad con la versión 3.6 de Python. Use la versión Python 3.5 o anteriores. |
| [IronPython](https://github.com/IronLanguages/ironpython2) | Implementación de .NET de Python, disponible en versiones de 32 y 64 bits, que proporciona interoperabilidad con C#, F# y Visual Basic, acceso a las API de .NET, depuración estándar de Python (pero no depuración en modo mixto de C++) y depuración mixta de IronPython y C#. IronPython, sin embargo, no admite entornos virtuales. |
| [Anaconda](https://www.continuum.io) | Plataforma de ciencia de datos abierta con tecnología de Python que incluye la versión más reciente de CPython y la mayoría de los paquetes de difícil instalación. Es la opción recomendable si no puede decidirse. |
| [PyPy](http://www.pypy.org/) | Implementación JIT de seguimiento de alto rendimiento de Python adecuada para programas de ejecución prolongada y situaciones donde se identifican problemas de rendimiento pero no puede encontrar otras resoluciones. Funciona con Visual Studio, pero con compatibilidad limitada para características de depuración avanzadas. |
| [Jython](http://www.jython.org/) | Implementación de Python en la Máquina virtual Java (JVM). Es similar a IronPython, donde el código que se ejecuta en Jython puede interactuar con clases y bibliotecas de Java, pero no es posible que no pueda utilizar muchas bibliotecas pensadas para CPython. Funciona con Visual Studio, pero con compatibilidad limitada para características de depuración avanzadas. |

Los desarrolladores que desean proporcionar nuevas formas de detección para entornos de Python pueden consultar [PTVS Environment Detection](https://github.com/Microsoft/PTVS/wiki/Extensibility-Environments) (Entorno detección PTVS) en github.com.

## <a name="managing-python-environments-in-visual-studio"></a>Administración de entornos de Python en Visual Studio

Para abrir la ventana Entornos de Python, seleccione el comando de menú **Vista > Otras ventanas > Entornos de Python** o haga clic con el botón derecho en el nodo **Entornos de Python** de un proyecto en el Explorador de soluciones y seleccione **Ver todos los entornos de Python**:

    ![View All Environments command in Solution Explorer](media/environments-view-all.png)

En cualquier caso, la ventana Python Environments (Entornos de Python) aparece como una pestaña del mismo nivel que el Explorador de soluciones:

![Ventana Python Environments (Entornos de Python)](media/environments-default-view.png)

En el ejemplo anterior se muestra que Python 3.4 (32-bit CPython) está instalado junto con versiones de 32 y 64 bits de IronPython 2.7. El entorno predeterminado en negrita es Python 3.4, que se usa para los nuevos proyectos. Si no ve ningún entorno en la lista, significa que ha instalado las Herramientas de Python para Visual Studio en Visual Studio 2015 o anterior, pero no ha instalado un intérprete de Python (consulte la sección anterior [Selección e instalación de los intérpretes de Python](#selecting-and-installing-python-interpreters)). El comando **+ Personalizado...** le permite [crear un entorno para un intérprete existente](#create-an-environment-for-an-existing-interpreter).

A la derecha de cada entorno de la lista figura un control que abre una ventana interactiva para ese entorno. Puede aparecer otro control que actualiza la base de datos de IntelliSense para ese entorno.

Debajo de la lista de entornos hay un selector desplegable para las opciones **Introducción**, **Paquetes** e **IntelliSense** que se describen más adelante en esta sección. Si expande la ventana **Entornos de Python** con un ancho suficiente, estas opciones se muestran como pestañas, lo cual puede resultarle más cómodo:

![Vista de la ventana Python Environments (Entornos de Python) expandida](media/environments-expanded-view.png)

> [!Note]
> Aunque Visual Studio respeta la opción de paquetes de sitio de sistema, no ofrece una forma de cambiarla desde dentro de Visual Studio.

Para ver un vídeo de introducción a la administración de entornos en Visual Studio, consulte [Managing Python Environments](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=qrDmN4LWE_8305918567) (Administrar entornos de Python) (Microsoft Virtual Academy, 2 min 35 s).

> [!VIDEO https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Managing-Python-Environments-qrDmN4LWE_8305918567]

### <a name="creating-an-environment-for-an-existing-interpreter"></a>Creación de un entorno para un intérprete existente

Si Visual Studio no encuentra un intérprete (por ejemplo, cuando se instala en una ubicación no estándar), puede crear un entorno como sigue:

1. Seleccione **+Personalizado...** en la ventana [Python Environments](#managing-python-environments-in-visual-studio) (Entornos de Python) para crear un nuevo entorno y abrir la pestaña [**Configurar**](#configure-tab) que se describe a continuación.

    ![Vista predeterminada para un nuevo entorno personalizado](media/environments-custom-1.png)

1. Escriba un nombre para el entorno en el campo **Descripción**.
1. Escriba o busque la ruta de acceso del intérprete en el campo **Prefix Path** (Ruta de acceso de prefijo).
1. Seleccione **Detección automática** para que Visual Studio complete los campos restantes o complételos manualmente.
1. Seleccione **Aplicar** para guardar el entorno.
1. Si necesita quitar el entorno, seleccione el comando **Quitar** en la pestaña **Configurar**. Los entornos detectados automáticamente no proporcionan esta opción. Para más información, consulte la sección siguiente.

### <a name="moving-an-existing-interpreter"></a>Traslado de un intérprete existente

Si mueve un intérprete existente a una nueva ubicación en el sistema de archivos, Visual Studio no detecta automáticamente el cambio y debe actualizar su entorno manualmente:

- Si ya creó un entorno para ese intérprete, modifique dicho entorno para que apunte a la nueva ubicación.

- Si originalmente el entorno se detectó automáticamente, se instaló en el equipo con un programa de instalación distinto que creó las entradas del Registro que examina Visual Studio. En este caso, restaure primero el intérprete de Python a su ubicación original. Después, desinstálelo mediante el instalador, que borra las entradas del Registro. A continuación, vuelva a instalar el intérprete en la ubicación deseada. Reinicie Visual Studio y debería detectar automáticamente la nueva ubicación. Este proceso garantiza que cualquier otro efecto secundario del instalador se aplica correctamente.

### <a name="overview-tab"></a>Pestaña Información general

Proporciona información básica y comandos para el entorno:

![Ficha Información general de entornos de Python](media/environments-overview-tab.png)

| Comando | Description |
| --- | --- |
| Hacer que este entorno sea el predeterminado para los proyectos nuevos | Establece el entorno activo, que puede hacer que Visual Studio deje de responder por unos instantes mientras se carga la base de datos de IntelliSense. Los entornos con muchos paquetes pueden dejar de responder durante más tiempo. |
| Visitar el sitio web del distribuidor | Abre un explorador en la URL proporcionada por la distribución de Python. Python 3.x, por ejemplo, se dirige a python.org. |
| Abrir ventana interactiva | Abre la [ventana interactiva (REPL)](interactive-repl.md) para este entorno en Visual Studio, aplicando cualquiera de los [scripts de inicio (ver a continuación)](#startup-scripts). |
| Explorar scripts interactivos | Vea [Scripts de inicio](#startup-scripts). |
| Usar el modo interactivo de IPython | Cuando se establece, se abre la ventana interactiva con IPython de manera predeterminada. Esto habilita los gráficos en línea así como la sintaxis de IPython extendida como `name?` para ver la Ayuda y `!command` para los comandos del shell. Esta opción se recomienda al usar una distribución de Anaconda, ya que necesita paquetes adicionales. Para obtener más información, vea [Uso de IPython en la ventana interactiva](interactive-repl-ipython.md). |
| Abrir en PowerShell | Inicie el intérprete en una ventana de comandos de PowerShell. |
| (Vínculos de carpeta) | Le proporcionan acceso rápido a la carpeta de instalación del entorno, al intérprete python.exe y al intérprete pythonw.exe. La primera se abre en Explorador de Windows, los dos últimos abren una ventana de consola. |

#### <a name="startup-scripts"></a>Scripts de inicio

A medida que usa las ventanas interactivas en su flujo de trabajo diario, probablemente desarrolle funciones auxiliares que usa con frecuencia. Por ejemplo, puede crear una función que abra un DataFrame en Excel y, después, guardar ese código como un script de inicio de manera que siempre esté disponible en la ventana interactiva.

Los scripts de inicio contienen código que la ventana interactiva carga y ejecuta automáticamente, como importaciones, definiciones de función y literalmente cualquier otra cosa. Hay dos maneras de hacer referencia a dichos scripts:

1. Cuando instala un entorno, Visual Studio crea una carpeta `Documents\Visual Studio 2017\Python Scripts\<environment>` donde &lt;environment> coincide con el nombre del entorno. Puede navegar fácilmente a la carpeta específica del entorno con el comando **Explorar scripts interactivos**. Cuando inicie la ventana interactiva para ese entorno, se cargan y ejecutan los archivos de `.py` que se encuentran aquí en orden alfabético.

1. El control **Scripts** de la pestaña **Herramientas > Opciones > Herramientas de Python > Ventanas interactivas** (vea [Opciones de ventanas interactivas](options.md#interactive-windows-options)) pretende especificar una carpeta adicional para los scripts de inicio que se cargan y ejecutan en todos los entornos. No obstante, esta característica no funciona actualmente.

### <a name="configure-tab"></a>Pestaña Configurar

Si se muestra, contiene detalles como se describe en la tabla siguiente. Si esta pestaña no está presente, significa que Visual Studio administra todos los detalles automáticamente.

![Pestaña Configuración de entornos de Python](media/environments-configure-tab.png)

| Campo | Description |
| --- | --- |
| **Descripción** | Nombre que se va a dar al entorno. |
| **Prefix path** (Ruta de acceso de prefijo) | Ubicación de la carpeta base del intérprete. Si rellena este valor y hace clic en **Detección automática**, Visual Studio intentará rellenar los demás campos automáticamente. |
| **Interpreter path** (Ruta de acceso del intérprete) | Ruta de acceso al ejecutable del intérprete, normalmente la ruta de acceso de prefijo seguida de `python.exe`. |
| **Windowed interpreter** (Intérprete en ventanas) | Ruta de acceso al ejecutable que no es de consola, normalmente la ruta de acceso de prefijo seguida de `pythonw.exe`. |
| **Library path** (Ruta de acceso a la biblioteca) | Especifica la raíz de la biblioteca estándar, pero este valor se puede omitir si Visual Studio es capaz de solicitar una ruta de acceso más precisa desde el intérprete. |
| **Versión de lenguaje** | Se selecciona en el menú desplegable. |
| **Arquitectura** | Normalmente se detecta y rellena automáticamente; de lo contrario especifica 32 o 64 bits. |
| **Path environment variable** (Variable de entorno de ruta de acceso) | Variable de entorno que el intérprete usa para encontrar rutas de acceso de búsqueda. Visual Studio cambia el valor de la variable al iniciar Python para que contenga las rutas de búsqueda del proyecto. Normalmente, esta propiedad se debe establecer en `PYTHONPATH`, pero algunos intérpretes utilizan un valor diferente. |

### <a name="pip-tab"></a>Pestaña pip

Administra los paquetes instalados en el entorno, lo que también permite buscar e instalar otros nuevos (incluidas las dependencias). La búsqueda filtra los paquetes instalados actualmente y [PyPI](https://pypi.python.org). También puede especificar cualquier comando `pip install` en el cuadro de búsqueda directamente, incluidas marcas, como `--user` o `--no-deps`.

![Pestaña pip de entornos de Python](media/environments-pip-tab.png)

Al instalar un paquete se crean subcarpetas dentro de la carpeta `Lib` del entorno en el sistema de archivos. Por ejemplo, si tiene instalado Python 3.6 en `c:\Python36`, los paquetes se instalan en `c:\Python36\Lib`; si tiene instalado Anaconda3 en `c:\Program Files\Anaconda3`, los paquetes se instalan en `c:\Program Files\Anaconda3\Lib`.

En el último caso, como el entorno está situado en un área protegida del sistema de archivos, `c:\Program Files`, Visual Studio debe ejecutar `pip install` con permisos elevados para permitirle que cree subcarpetas del paquete. Cuando se necesita la elevación de privilegios, Visual Studio muestra el mensaje "Puede que se necesiten privilegios de administrador para instalar, actualizar o desinstalar paquetes para este entorno":

![Mensaje de elevación de privilegios para la instalación del paquete](media/environments-pip-elevate.png)

**Elevar ahora** concede privilegios administrativos a pip para una única operación, sujeto también a cualquier sistema operativo que solicite permisos. Al seleccionar **Continuar sin privilegios de administrador** se intenta instalar el paquete, pero pip produce un error al intentar crear carpetas con un resultado como "Error: no se pudo crear 'C:\Program Files\Anaconda3\Lib\site-packages\png.py': permiso denegado".

Al seleccionar **Elevar siempre al instalar o desinstalar paquetes** se impide que el cuadro de diálogo aparezca para el entorno en cuestión. Para que el cuadro de diálogo aparezca de nuevo, vaya a **Herramientas > Opciones > Herramientas de Python > General** y seleccione el botón **Restablecer todos los cuadros de diálogo ocultos de manera permanente**.

En esa misma pestaña de opciones, también puede seleccionar **Ejecutar siempre pip como administrador** para suprimir el cuadro de diálogo en todos los entornos. Vea [Opciones: pestaña General](options.md#general-options).

### <a name="intellisense-tab"></a>Pestaña IntelliSense

Muestra el estado actual de la base de datos de finalización de IntelliSense:

![Pestaña IntelliSense de entornos de Python](media/environments-intellisense-tab.png)

La base de datos contiene metadatos para todas las bibliotecas del entorno, mejora la velocidad de IntelliSense y reduce el uso de memoria. Cuando Visual Studio detecta un nuevo entorno (o el usuario agrega uno), comienza a compilar automáticamente la base de datos analizando los archivos de origen de la biblioteca. Este proceso puede tardar desde un minuto a una hora o más dependiendo de lo que esté instalado. (Anaconda, por ejemplo, incluye muchas bibliotecas y tarda algún tiempo en compilar la base de datos.) Una vez finalizado, obtiene detalles de IntelliSense y no necesita actualizar la base de datos (con el botón **Refresh DB** (Actualizar base de datos)) hasta que instale más bibliotecas.

Las bibliotecas para las que no se han compilado los datos se marcan con **!**; si la base de datos de un entorno no está completa, también aparece **!** junto a ella en la lista principal de entornos.

## <a name="selecting-an-environment-for-a-project"></a>Selección de un entorno para un proyecto

Los entornos específicos del proyecto garantizan que un proyecto siempre se ejecuta en un entorno concreto, pasando por alto el entorno global predeterminado. Por ejemplo, si el entorno predeterminado global es CPython, pero un proyecto necesita IronPython y determinadas bibliotecas que no están instaladas en el entorno global, entonces se necesita un entorno específico del proyecto.

Los entornos del proyecto se muestran en el Explorador de soluciones bajo el nodo Python Environments (Entornos de Python). La entrada en negrita está activa actualmente y Visual Studio la usa para la depuración, las finalizaciones de importación y miembros, la comprobación de sintaxis y cualquier otra tarea que necesite un entorno:

![Entornos del proyecto mostrados en el Explorador de soluciones](media/environments-project.png)

Para activar un entorno diferente para el proyecto, haga clic con el botón derecho en ese entorno y seleccione **Activate Environment** (Activar entorno).

Cualquier entorno global se puede agregar como un entorno de proyecto haciendo clic con el botón derecho en **Python Environments** (Entornos de Python) y seleccionando **Add/Remove Python Environments...** (Agregar o quitar entornos de Python...). En la lista mostrada puede seleccionar aquellos entornos que estén disponibles en el proyecto, así como anular la selección de los mismos.

![Cuadro de diálogo Add/Remove Python Environments (Agregar o quitar entornos de Python)](media/environments-add-remove.png)

En el Explorador de soluciones, también puede expandir el entorno para mostrar sus paquetes instalados (aquellos que puede importar y utilizar en el código cuando el entorno está activo):

![Paquetes de Python para un entorno en el Explorador de soluciones](media/environments-installed-packages.png)

Para instalar nuevos paquetes, haga clic con el botón derecho en el entorno, seleccione **Install Python Package…**  (Instalar paquete de Python...) y escriba el nombre del paquete deseado. Los paquetes (y las dependencias) se descargan desde [Python Package Index (PyPI)](https://pypi.python.org/pypi), donde también puede buscar paquetes disponibles. La barra de estado de Visual Studio y la ventana de salida muestran información sobre la instalación. Para desinstalar un paquete, haga clic con el botón derecho en él y seleccione **Quitar**.

> [!Note]
> El equipo de desarrollo principal de Python está actualmente trabajando en la compatibilidad con la administración de paquetes de Python. Las entradas mostradas puede que no sean siempre precisas, y la instalación y desinstalación pueden no ser confiables o estar disponibles. Visual Studio usa el administrador de paquetes de pip si está disponible y lo descarga e instala cuando sea necesario. Visual Studio también puede usar el administrador de paquetes de easy_install. También se muestran los paquetes instalados con pip o easy_install desde la línea de comandos.

> [!Tip]
> Una situación común donde pip no puede instalar un paquete es cuando este incluye código fuente para componentes nativos en archivos `*.pyd`. Sin la versión necesaria de Visual Studio instalada, pip no puede compilar estos componentes. El mensaje de error que se muestra en esta situación es `error: Unable to find vcvarsall.bat`. `easy_install` suele poder descargar los binarios previamente compilados, y el usuario puede descargar un compilador adecuado para versiones anteriores de Python de [http://aka.ms/VCPython27](http://aka.ms/VCPython27). Para más información, consulte [How to deal with the pain of "unable to find vcvarsallbat"](https://blogs.msdn.microsoft.com/pythonengineering/2016/04/11/unable-to-find-vcvarsall-bat/) (Cómo afrontar la dificultad de "no poder encontrar vcvarsallbat") en el blog del equipo de herramientas de Python.

## <a name="creating-virtual-environments"></a>Creación de entornos virtuales

1. Haga clic con el botón derecho en **Python Environments** (Entornos de Python) en el Explorador de soluciones y seleccione **Add Virtual Environment…** (Agregar entorno virtual…); se mostrará lo siguiente:

    ![Creación de un entorno virtual](media/environments-add-virtual-1.png)

1. Especifique un nombre para crear el entorno virtual en la ruta de acceso del proyecto o una ruta de acceso completa para crearlo en cualquier otro lugar. (Para garantizar la máxima compatibilidad con otras herramientas, use solo letras y números en el nombre.)

1. Seleccione un entorno global como intérprete base y haga clic en **Crear**. Si los paquetes `pip` y `virtualenv` o `venv` no están disponibles, se descargan e instalan.

    Si la ruta de acceso proporcionada es un entorno virtual existente, se detecta el intérprete base y el botón Crear cambia a **Agregar**:

    ![Incorporación de un entorno virtual existente](media/environments-add-virtual-2.png)

También se puede agregar un entorno virtual existente haciendo clic con el botón derecho en **Python Environments** (Entornos de Python) en el Explorador de soluciones y seleccionando **Add Existing Virtual Environment...** (Agregar entorno virtual existente...). Visual Studio detecta automáticamente el intérprete base mediante el archivo `orig-prefix.txt` en el directorio del entorno `lib`.

Una vez que un entorno virtual se agrega al proyecto y aparece en la ventana **Python Environments** (Entornos de Python), puede activarlo como cualquier otro entorno y administrar sus paquetes. Si hace clic con el botón derecho en él y selecciona **Quitar**, quitará la referencia al entorno o eliminará el entorno y todos sus archivos en disco (pero no el intérprete base).

Tenga en cuenta que un inconveniente de los entornos virtuales es que contienen rutas de acceso a archivos codificadas de forma rígida y, por tanto, no es fácil compartirlos o transportarlos a otros equipos de desarrollo. Afortunadamente, puede usar el archivo `requirements.txt` tal como se describe en la sección siguiente para permitir que los destinatarios de su proyecto restauren fácilmente el entorno.

## <a name="managing-required-packages-requirementstxt"></a>Administración de paquetes necesarios (requirements.txt)

Si comparte un proyecto con otros usuarios mediante un sistema de compilación o pretende [publicarlo en Microsoft Azure](template-azure-cloud-service.md), necesita especificar los paquetes externos que dicho proyecto requiere. El enfoque recomendado es usar un [archivo requirements.txt](http://pip.readthedocs.org/en/latest/user_guide.html#requirements-files) (readthedocs.org) que contiene una lista de comandos para pip que instala las versiones necesarias de los paquetes dependientes.

Técnicamente, se puede utilizar cualquier nombre de archivo para realizar un seguimiento de los requisitos (mediante el uso de `-r <full path to file>` al instalar un paquete), pero Visual Studio proporciona compatibilidad específica para `requirements.txt`:

- Si ha cargado un proyecto que contiene `requirements.txt` y desea instalar todos los paquetes enumerados en ese archivo, expanda el nodo **Python Environments** en el **Explorador de soluciones** y, luego, haga clic con el botón derecho en un nodo de entorno y seleccione **Install from requirements.txt** (Instalar desde requirements.txt):

    ![Instalar desde requirements.txt](media/environments-requirements-txt-install.png)

- Si ya tiene todos los paquetes necesarios instalados en un proyecto, puede hacer clic con el botón derecho en un entorno en el Explorador de soluciones y seleccionar **Generate requirements.txt** (Generar requirements.txt) para crear el archivo necesario. Si el archivo ya existe, aparece un mensaje sobre cómo actualizarlo:

    ![Opciones de actualización de requirements.txt](media/environments-requirements-txt-replace.png)

  - **Replace entire file** (Reemplazar todo el archivo) quita todos los elementos, comentarios y opciones que existen.
  - **Actualizar entradas existentes** detecta los requisitos del paquete y actualiza los especificadores de versión para que coincidan con la versión actualmente instalada.
  - **Update and add entries** (Actualizar y agregar entradas) actualiza todos los requisitos que se encuentran y agrega todos los demás paquetes al final del archivo.

Dado que los archivos `requirements.txt` están pensados para inmovilizar los requisitos del proyecto, todos los paquetes instalados se escriben con versiones precisas. Usar versiones precisas garantiza que puede reproducir fácilmente el entorno en otro equipo. Los paquetes se incluyen aunque se instalaran con un intervalo de versiones, como una dependencia de otro paquete, o con un instalador distinto de pip.

Si existe un archivo `requirements.txt` cuando se agrega un nuevo entorno virtual, el cuadro de diálogo **Agregar entorno virtual** mostrará una opción para instalar los paquetes de manera automática, lo que facilita volver a crear un entorno en otro equipo:

![Creación de un entorno virtual con requirements.txt](media/environments-requirements-txt.png)

Si un paquete no se puede instalar mediante pip y aparece en un archivo `requirements.txt`, toda la instalación produce un error. En este caso, edite manualmente el archivo para excluir este paquete o para usar [opciones de pip](http://pip.readthedocs.org/en/latest/reference/pip_install.html#requirements-file-format) para hacer referencia a una versión instalable del paquete. Por ejemplo, puede ser preferible usar [`pip wheel`](http://pip.readthedocs.org/en/latest/reference/pip_wheel.html) para compilar una dependencia y agregar la opción `--find-links <path>` a su `requirements.txt`:

```output
C:\Project>pip wheel azure
Downloading/unpacking azure
    Running setup.py (path:C:\Project\env\build\azure\setup.py) egg_info for package azure

Building wheels for collected packages: azure
    Running setup.py bdist_wheel for azure
    Destination directory: c:\project\wheelhouse
Successfully built azure
Cleaning up...

C:\Project>type requirements.txt
--find-links wheelhouse
--no-index
azure==0.8.0

C:\Project>pip install -r requirements.txt -v
Downloading/unpacking azure==0.8.0 (from -r requirements.txt (line 3))
    Local files found: C:/Project/wheelhouse/azure-0.8.0-py3-none-any.whl
Installing collected packages: azure
Successfully installed azure
Cleaning up...
    Removing temporary dir C:\Project\env\build...
```

## <a name="search-paths"></a>Rutas de acceso de búsqueda

Con un uso típico de Python, la variable de entorno `PYTHONPATH` (o `IRONPYTHONPATH`, etc.) proporciona la ruta de acceso de búsqueda predeterminada para los archivos de módulo. Es decir, cuando usa una instrucción `from <name> import...`or`import <name>`, Python busca un nombre coincidente en las siguientes ubicaciones en orden:

1. Módulos integrados de Python.
1. La carpeta que contiene el código de Python que está ejecutando.
1. La "ruta de acceso de búsqueda de módulo" tal y como la definió la variable de entorno aplicable. (Consulte [The Module Search Path](https://docs.python.org/2/tutorial/modules.html#the-module-search-path) (Ruta de acceso de búsqueda de módulos) y [Environment variables](https://docs.python.org/2/using/cmdline.html#envvar-PYTHONPATH) (Variables de entorno) en la documentación principal de Python).

Sin embargo, Visual Studio omite la variable de entorno de ruta de acceso de búsqueda, incluso si se ha establecido para todo el sistema. De hecho, se omite precisamente *porque* se establece para todo el sistema y, por tanto, surgen determinadas preguntas que no se pueden responder automáticamente: ¿Están los módulos a los que se hace referencia diseñados para Python 2.7 o Python 3.3? ¿Van a invalidar a los módulos de biblioteca estándar? ¿Es consciente el desarrollador de este comportamiento o se trata de un intento de secuestro de sesión malintencionado?

Visual Studio proporciona así un medio para especificar rutas de acceso de búsqueda directamente tanto en entornos como en proyectos. El código que ejecuta o depura en Visual Studio recibe rutas de acceso de búsqueda en el valor de `PYTHONPATH` (y otras variables equivalente). Mediante la incorporación de rutas de acceso de búsqueda, Visual Studio inspecciona las bibliotecas en estas ubicaciones y crea bases de datos de IntelliSense para ellas (crear la base de datos puede tardar algún tiempo dependiendo del número de bibliotecas).

Para agregar una ruta de búsqueda, haga clic con el botón derecho en el elemento **Rutas de búsqueda** en el Explorador de soluciones, seleccione **Add Folder to Search Path…** (Agregar carpeta a ruta de acceso de búsqueda…) y seleccione la carpeta que desea incluir. Esta ruta de acceso se utiliza para cualquier entorno asociado al proyecto. (Puede ver errores si el entorno se basa en Python 3 e intenta agregar una ruta de acceso de búsqueda a los módulos de Python 2.7).

Los archivos con una extensión `.zip` o `.egg` también se pueden agregar como rutas de acceso de búsqueda seleccionando **Add Zip Archive to Search Path…** (Agregar archivo Zip a la ruta de acceso de búsqueda…). Al igual que con las carpetas, el contenido de estos archivos se examina y se pone a disposición de IntelliSense.

Si utiliza periódicamente las mismas rutas de acceso de búsqueda y el contenido no cambia con frecuencia, puede ser más eficaz instalarlo en la carpeta de paquetes del sitio. La ruta de acceso de búsqueda se analiza y almacena después en la base de datos de IntelliSense, siempre se asocia con el entorno deseado y no requiere que se agregue una ruta de acceso de búsqueda para cada proyecto.
