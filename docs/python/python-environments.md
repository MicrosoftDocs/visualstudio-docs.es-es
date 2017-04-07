---
title: Entornos de Python en Herramientas de Python para Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8876f8c1-4770-44dc-97d8-bf0035ae8196
caps.latest.revision: 11
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 7d726441c2d6953bd7b50451bec7fff05d5d71b0
ms.openlocfilehash: 69740c73cc133e08254fc546d2b59885270725f2
ms.lasthandoff: 03/10/2017

---

# <a name="python-environments"></a>Entornos de Python

El código Python siempre se ejecuta dentro de un determinado *entorno* de Python, que consta de un intérprete, una biblioteca (normalmente la biblioteca estándar de Python) y un conjunto de paquetes instalados. Todos estos elementos juntos determinan qué construcciones de lenguaje y sintaxis son válidas, a qué funcionalidad de sistema operativo puede acceder y qué paquetes puede utilizar.

La carga de trabajo de Python en Visual Studio facilita la administración de varios entornos de Python y cambia fácilmente entre ellos para proyectos diferentes. Un entorno también incluye una base de datos de IntelliSense para las bibliotecas de un entorno, de forma que la escritura de una instrucción como `import` en el editor de Visual Studio mostrará automáticamente una lista de bibliotecas disponibles así como los módulos que hay dentro de esas bibliotecas.

A menudo, los desarrolladores usan un único entorno de Python global, pero otras personas necesitan administrar varios entornos globales, entornos específicos del proyecto y quizás también entornos virtuales, como se explica en este tema:

- [Selección e instalación de los intérpretes de Python](#selecting-and-installing-python-interpreters)
- [Administración de entornos de Python en Visual Studio](#managing-python-environments-in-visual-studio)
- [Entornos globales](#global-environments)
- [Entornos específicos del proyecto](#project-specific-environments)
- [Entornos virtuales](#virtual-environments)
- [Administración de paquetes necesarios](#managing-required-packages)
- [Rutas de acceso de búsqueda](#search-paths)

Para obtener una introducción, consulte el vídeo de youtube.com (13 minutos y 27 segundos) [Deep Dive: Python Interpreters](https://youtu.be/KY1GEOo3qy0) (Profundización: intérpretes de Python).

> [!VIDEO https://www.youtube.com/embed/KY1GEOo3qy0]

## <a name="selecting-and-installing-python-interpreters"></a>Selección e instalación de los intérpretes de Python

Excepto con Visual Studio 2017 Preview, la compatibilidad de Python no incluye un intérprete de Python, por lo que necesita instalar uno de los siguientes para ejecutar el código. En general, Visual Studio detectará automáticamente intérpretes recién instalados y configurará un entorno para ellos. Si no es así, consulte la sección [Creación de un entorno para un intérprete existente](#creating-an-environment-for-an-existing-interpreter) a continuación.

| Intérprete | Descripción | 
| --- | --- | 
| [CPython](https://www.python.org/) | Intérprete "nativo" y que se usa con más frecuencia, disponible en versiones de 32 y 64 bits (se recomienda la versión de 32 bits). Incluye características más recientes del lenguaje, máxima compatibilidad con paquetes de Python, compatibilidad completa con la depuración e interoperabilidad con [IPython](http://ipython.org/). Consulte también: [Should I use Python 2 or Python 3?](http://wiki.python.org/moin/Python2orPython3) (¿Debo utilizar Python 2 o Python 3?) |
| [IronPython](http://ironpython.codeplex.com/) | Implementación de .NET de Python, disponible en versiones de 32 y 64 bits, que proporciona interoperabilidad con C#, F# y Visual Basic, acceso a las API. NET, depuración estándar de Python (pero no depuración en modo mixto de C++) y depuración mixta de IronPython y C#. IronPython, sin embargo, no admite entornos virtuales. | 
| [Anaconda](https://www.continuum.io) | Plataforma de ciencia de datos abierta con tecnología de Python que incluye la versión más reciente de CPython y la mayoría de los paquetes de difícil instalación. Es la opción recomendable si no puede decidirse. |
| [PyPy](http://www.pypy.org/) | Implementación JIT de seguimiento de alto rendimiento de Python adecuada para programas de ejecución prolongada y situaciones donde se identifican problemas de rendimiento pero no puede encontrar otras resoluciones. Funciona con Visual Studio, pero con compatibilidad limitada para características de depuración avanzadas. |
| [Jython](http://www.jython.org/) | Implementación de Python en la Máquina virtual Java (JVM). Es similar a IronPython, donde el código que se ejecuta en Jython puede interactuar con clases y bibliotecas de Java, pero no es posible que no pueda utilizar muchas bibliotecas pensadas para CPython. Funciona con Visual Studio, pero con compatibilidad limitada para características de depuración avanzadas. |

Los desarrolladores que desean proporcionar nuevas formas de detección para entornos de Python pueden consultar [PTVS Environment Detection](https://github.com/Microsoft/PTVS/wiki/Extensibility-Environments) (Entorno detección PTVS) en github.com.

## <a name="managing-python-environments-in-visual-studio"></a>Administración de entornos de Python en Visual Studio

Para abrir la ventana Python Environments (Entornos de Python), realice una de las siguientes acciones:

1. Seleccione el comando de menú **Vista > Otras ventanas > Entornos de Python (Entornos de Python)**.
1. Haga clic con el botón derecho en **Python Environments** (Entornos de Python) para un proyecto en el Explorador de soluciones y seleccione **View All Python Environments** (Ver todos los entornos de Python):

    ![Comando Ver todos los entornos del Explorador de soluciones](media/environments-view-all.png)
    
En cualquier caso, la ventana Python Environments (Entornos de Python) aparece como una pestaña del mismo nivel que el Explorador de soluciones:

![Ventana Python Environments (Entornos de Python)](media/environments-default-view.png)

En el ejemplo anterior, tenemos Python 3.4 (CPython de 32 bits) instalado junto con versiones de 32 y 64 bits de IronPython. El entorno predeterminado en negrita es Python 3.4, que se utilizará para los proyectos nuevos. Si no ve ningún entorno en la lista, significa que ha instalado las Herramientas de Python para Visual Studio pero no ha instalado un intérprete de Python (consulte la sección [Selección e instalación de los intérpretes de Python](#selecting-and-installing-python-interpreters) anterior).

> [!Tip]
> Cuando la ventana **Python Environments* (Entornos de Python) sea estrecha, como se muestra anteriormente, los entornos se muestran en la parte superior y las distintas pestañas en la parte inferior. Sin embargo, si expande la ventana lo suficiente, verá una vista amplia que puede resultarle más cómoda para trabajar.
>
> ![Vista de la ventana Python Environments (Entornos de Python) expandida](media/environments-expanded-view.png)

Visual Studio normalmente localiza un intérprete de Python instalado comprobando el registro, pero puede no encontrarlo si el intérprete está instalado de un modo no estándar. En tales casos, puede apuntar Visual Studio directamente al intérprete de la siguiente manera:

1. Seleccione **+Personalizado...** en la ventana Python Environments (Entornos de Python) para crear un nuevo entorno y abrir la pestaña [**Configurar**](#configure-tab) que se describe a continuación.

    ![Vista predeterminada para un nuevo entorno personalizado](media/environments-custom-1.png)

1. Escriba un nombre para el entorno en el campo **Descripción**.
1. Escriba o busque la ruta de acceso del intérprete en el campo **Prefix Path** (Ruta de acceso de prefijo).
1. Seleccione **Detección automática** para que Visual Studio complete los campos restantes o complételos manualmente.
1. Seleccione **Aplicar** para guardar el entorno.
1. Si necesita quitar el entorno, seleccione el comando **Quitar** en la pestaña **Configurar**.

> [!Note]
> Aunque Visual Studio respeta la opción de paquetes de sitio de sistema, no ofrece una forma de cambiarla desde dentro de Visual Studio.

### <a name="overview-tab"></a>Pestaña Información general

Proporciona información básica y comandos para el entorno, como el establecimiento de este como el entorno predeterminado, la apertura de una [ventana interactiva (REPL)](interactive-repl.md) con ese entorno y el salto al cuadro de diálogo para configurar la ventana interactiva (igual que el comando de menú **Herramientas > Opciones**, seleccionando **Herramientas de Python > Ventanas interactivas** y el nombre del entorno).

![Ficha Información general de entornos de Python](media/environments-overview-tab.png)

> [!Note]
> El cambio de entorno activo puede hacer que Visual Studio deje de responder por unos instantes mientras se carga la base de datos de IntelliSense. Los entornos con muchos paquetes pueden dejar de responder durante más tiempo.

### <a name="configure-tab"></a>Pestaña Configurar

Si se muestra, contiene detalles como se describe en la tabla siguiente. Si esta pestaña no está presente, significa que Visual Studio administra todos los detalles automáticamente.

![Pestaña Configuración de entornos de Python](media/environments-configure-tab.png)

| Campo | Descripción |
| --- | --- |
| **Descripción** | Nombre que se va a dar al entorno. |
| **Prefix path** (Ruta de acceso de prefijo) | Ubicación de la carpeta base del intérprete. Si rellena esta información y hace clic en **Detección automática**, Visual Studio intentará rellenar los demás campos automáticamente. |
| **Interpreter path** (Ruta de acceso del intérprete) | Ruta de acceso al ejecutable del intérprete, normalmente la ruta de acceso de prefijo seguida de `python.exe`. |
| **Windowed interpreter** (Intérprete en ventanas) | Ruta de acceso al ejecutable que no es de consola, normalmente la ruta de acceso de prefijo seguida de `pythonw.exe`. |
| **Library path** (Ruta de acceso a la biblioteca) | Especifica la raíz de la biblioteca estándar, pero este valor se puede omitir si Visual Studio es capaz de solicitar una ruta de acceso más precisa desde el intérprete. |
| **Versión de lenguaje** | Se selecciona en el menú desplegable. |
| **Arquitectura** | Normalmente se detecta y rellena automáticamente; de lo contrario especifica 32 o 64 bits. |
| **Path environment variable** (Variable de entorno de ruta de acceso) | Variable de entorno que el intérprete usa para encontrar rutas de acceso de búsqueda. Visual Studio cambia el valor de la variable al iniciar Python para que contenga las rutas de búsqueda del proyecto. Normalmente, esta propiedad se debe establecer en `PYTHONPATH`, pero algunos intérpretes utilizan un valor diferente. |

### <a name="pip-tab"></a>Pestaña pip

Administra los paquetes instalados en el entorno, lo que también permite buscar e instalar otros nuevos (incluidas las dependencias). La búsqueda filtrará los paquetes instalados actualmente, así como el índice de paquetes de Python ([PyPI](https://pypi.python.org)) de búsqueda. También puede especificar cualquier comando `pip install` en el cuadro de búsqueda directamente, incluidas marcas, como `--user` o `--no-deps`.

![Pestaña pip de entornos de Python](media/environments-pip-tab.png)

### <a name="intellisense-tab"></a>Pestaña IntelliSense

Muestra el estado actual de la base de datos de finalización de IntelliSense:

![Pestaña IntelliSense de entornos de Python](media/environments-intellisense-tab.png)

La base de datos contiene metadatos para todas las bibliotecas del entorno, mejora la velocidad de IntelliSense y reduce el uso de memoria. Cuando Visual Studio detecta un nuevo entorno (o el usuario agrega uno), comienza a compilar automáticamente la base de datos analizando los archivos de origen de la biblioteca. Este proceso puede tardar desde un minuto a una hora o más dependiendo de lo que esté instalado. (Anaconda, por ejemplo, incluye muchas bibliotecas y tarda algún tiempo en compilar la base de datos.) Una vez finalizado, obtendrá detalles de IntelliSense y no tendrá que volver a actualizar la base de datos (con el botón **Refresh DB** (Actualizar base de datos)) hasta que instale más bibliotecas.

Las bibliotecas para las que no se han compilado los datos se marcan con **!**; si la base de datos de un entorno no está completa, también aparece **!** junto a ella en la lista principal de entornos.

## <a name="global-environments"></a>Entornos globales

Los entornos globales (o de todo el sistema) están disponibles para todos los proyectos en una máquina. Visual Studio normalmente detecta entornos globales automáticamente, que se pueden ver en la ventana Python Environments (Entornos de Python). Si no es así, puede agregar un entorno manualmente, como se describió anteriormente en [Administración de entornos de Python en Visual Studio](#managing-python-environments-in-visual-studio).

Visual Studio usa el entorno predeterminado para todos los nuevos proyectos para ejecución, depuración, comprobación de la sintaxis, visualización de finalizaciones de importación y miembros y cualquier otra tarea que requiera un entorno. El cambio del entorno predeterminado afectará a todos los proyectos a los que no se ha agregado un [entorno específico del proyecto](#project-specific-environments), tal como se describe a continuación.

## <a name="project-specific-environments"></a>Entornos específicos del proyecto

Los entornos específicos del proyecto garantizan que un proyecto siempre se ejecuta en un entorno concreto, pasando por alto el entorno global predeterminado. Por ejemplo, si el entorno predeterminado global es CPython, pero un proyecto necesita IronPython y determinadas bibliotecas que no están instaladas en el entorno global, entonces se necesita un entorno específico del proyecto.

Los entornos del proyecto se muestran en el Explorador de soluciones bajo el nodo Python Environments (Entornos de Python). La entrada en negrita está activa actualmente y se utilizará para depuración, finalizaciones de importación y miembros, comprobación de sintaxis y cualquier otra tarea que necesite un entorno:

![Entornos del proyecto mostrados en el Explorador de soluciones](media/environments-project.png)

Para activar un entorno diferente para el proyecto, haga clic con el botón derecho en ese entorno y seleccione **Activate Environment** (Activar entorno).

Cualquier entorno global se puede agregar como un entorno de proyecto haciendo clic con el botón derecho en **Python Environments** (Entornos de Python) y seleccionando **Add/Remove Python Environments...** (Agregar o quitar entornos de Python...). En la lista mostrada puede seleccionar aquellos que estén disponibles en el proyecto, así como anular la selección de los mismos.

![Cuadro de diálogo Add/Remove Python Environments (Agregar o quitar entornos de Python)](media/environments-add-remove.png)

En el Explorador de soluciones, también puede expandir el entorno para mostrar sus paquetes instalados (aquellos que puede importar y utilizar en el código cuando el entorno está activo):

![Paquetes de Python para un entorno en el Explorador de soluciones](media/environments-installed-packages.png)

Para instalar nuevos paquetes, haga clic con el botón derecho en el entorno, seleccione **Install Python Package…** (Instalar paquete de Python...) y escriba el nombre del paquete deseado. Los paquetes (y las dependencias) se descargan desde [Python Package Index (PyPI)](https://pypi.python.org/pypi), donde también puede buscar paquetes disponibles. La barra de estado de Visual Studio y la ventana de salida muestran información sobre la instalación. Para desinstalar un paquete, haga clic con el botón derecho en él y seleccione **Quitar**.

> [!Note]
> El equipo de desarrollo principal de Python está actualmente trabajando en la compatibilidad con la administración de paquetes de Python. Las entradas mostradas puede que no sean siempre precisas, y la instalación y desinstalación pueden no ser confiables o estar disponibles. Visual Studio usa el administrador de paquetes de pip si está disponible y lo descargará e instalará cuando sea necesario. Visual Studio también puede usar el administrador de paquetes de easy_install. También se muestran los paquetes instalados con pip o easy_install desde la línea de comandos.

> [!Tip]
> Una situación común donde pip no podrá instalar un paquete es cuando este incluye código fuente para componentes nativos en archivos `*.pyd`. Sin la versión necesaria de Visual Studio instalada, pip no podrá compilar estos componentes. El mensaje de error mostrado en esta situación es `error: Unable to find vcvarsall.bat.` `easy_install` suele poder descargar los binarios previamente compilados, y el usuario puede descargar un compilador adecuado para versiones anteriores de Python de [http://aka.ms/VCPython27](http://aka.ms/VCPython27). Para más información, consulte [How to deal with the pain of "unable to find vcvarsallbat"](https://blogs.msdn.microsoft.com/pythonengineering/2016/04/11/unable-to-find-vcvarsall-bat/) (Cómo afrontar la dificultad de "no poder encontrar vcvarsallbat") en el blog del equipo de herramientas de Python.


## <a name="virtual-environments"></a>Entornos virtuales

Debido a que los paquetes instalados en un entorno global están disponibles para todos los proyectos que lo usan, pueden haber conflictos cuando dos proyectos requieren paquetes incompatibles o versiones diferentes del mismo paquete. Para evitar tales conflictos, Visual Studio proporciona la capacidad de crear *entornos virtuales*, que normalmente son específicos para un proyecto.

Al igual que cualquier otro entorno de Python, un entorno virtual consta de una biblioteca, un conjunto de paquetes y un intérprete de Python. En este caso, sin embargo, el entorno virtual usa el intérprete y la biblioteca de uno de los entornos globales (siempre que admita entornos virtuales), pero sus paquetes son independientes y están aislados de los entornos globales y de todos los demás entornos virtuales. Una vez más, esto evita conflictos y minimiza el impacto del entorno virtual en el tamaño aproximado de sus paquetes. 

Para crear un entorno virtual:

1. Haga clic con el botón derecho en **Python Environments** (Entornos de Python) en el Explorador de soluciones y seleccione **Add Virtual Environment…** (Agregar entorno virtual…); se mostrará lo siguiente:

    ![Creación de un entorno virtual](media/environments-add-virtual-1.png)

1. Especifique un nombre para crear el entorno virtual en la ruta de acceso del proyecto o una ruta de acceso completa para crearlo en cualquier otro lugar. (Para garantizar la máxima compatibilidad con otras herramientas, use solo letras y números en el nombre.)

1. Seleccione un entorno global como intérprete base y haga clic en **Crear**. Si los paquetes `pip` y `virtualenv` o `venv` no están disponibles, se descargarán e instalarán.

    Si la ruta de acceso proporcionada es un entorno virtual existente, se detectará el intérprete base y el botón Crear cambiará a **Agregar**:

    ![Incorporación de un entorno virtual existente](media/environments-add-virtual-2.png)

También se puede agregar un entorno virtual existente haciendo clic con el botón derecho en **Python Environments** (Entornos de Python) en el Explorador de soluciones y seleccionando **Add Existing Virtual Environment...** (Agregar entorno virtual existente...). Visual Studio detecta automáticamente el intérprete base mediante el archivo `orig-prefix.txt` en el directorio del entorno `lib`.

Una vez que un entorno virtual se agrega al proyecto y aparece en la ventana **Python Environments** (Entornos de Python), puede activarlo como cualquier otro entorno y administrar sus paquetes. Si hace clic con el botón derecho en él y selecciona **Quitar**, quitará la referencia al entorno o eliminará el entorno y todos sus archivos en disco (pero no el intérprete base, por supuesto).

Tenga en cuenta que un inconveniente de los entornos virtuales es que contienen rutas de acceso a archivos codificadas de forma rígida y, por tanto, no es fácil compartirlos o transportarlos a otras máquinas de desarrollo. Afortunadamente, puede usar el archivo `requirements.txt` tal y como se describe en la sección siguiente.

## <a name="managing-required-packages"></a>Administración de paquetes necesarios

Si comparte un proyecto con otros usuarios, mediante un sistema de compilación, o pretende [publicarlo en Microsoft Azure](template-azure-cloud-service.md), necesitará especificar los paquetes externos que dicho proyecto requiere. El enfoque recomendado es usar un [archivo requirements.txt](http://pip.readthedocs.org/en/latest/user_guide.html#requirements-files) (readthedocs.org) que contiene una lista de comandos para pip que instalarán las versiones necesarias de los paquetes dependientes.

Técnicamente, se puede utilizar cualquier nombre de archivo para realizar un seguimiento de los requisitos (mediante el uso de `-r <full path to file>` al instalar un paquete), pero Visual Studio proporciona compatibilidad específica para `requirements.txt`:

- Si ha cargado un proyecto que contiene `requirements.txt` y desea instalar todos los paquetes enumerados en ese archivo, haga clic con el botón derecho en el proyecto y seleccione **Install from requirements.txt** (Instalar desde requirements.txt):

    ![Instalar desde requirements.txt](media/environments-requirements-txt-install.png)

- Cuando tenga todos los paquetes necesarios instalados en un proyecto, puede hacer clic con el botón derecho en dicho proyecto en el Explorador de soluciones y seleccionar **Generar requirements.txt** para crear el archivo necesario. Si el archivo ya existe, se le preguntará cómo actualizarlo:

    ![Opciones de actualización de requirements.txt](media/environments-requirements-txt-replace.png)

    - **Replace entire file** (Reemplazar todo el archivo) quita todos los elementos, comentarios y opciones que existen.
    - **Refresh existing entries** (Actualizar entradas existentes) detecta los requisitos del paquete y actualiza los especificadores de versión para que coincidan con la versión actualmente instalada.
    - **Update and add entries** (Actualizar y agregar entradas) actualiza todos los requisitos que se encuentran y agrega todos los demás paquetes al final del archivo.

Dado que los archivos `requirements.txt` están pensados para inmovilizar los requisitos del proyecto, todos los paquetes instalados se escriben con versiones precisas. Esto garantiza que puede reproducir fácilmente el entorno en otra máquina. Los paquetes se incluyen aunque se instalaran con un intervalo de versiones, como una dependencia de otro paquete, o con un instalador distinto de pip.

Cuando se agrega un nuevo entorno virtual, si existe un archivo ` requirements.txt`, el cuadro de diálogo **Add Virtual Environment** (Agregar entorno virtual) muestra una opción para instalar los paquetes de forma automática, lo que facilita volver a crear un entorno en otra máquina:

![Creación de un entorno virtual con requirements.txt](media/environments-requirements-txt.png)

Si un paquete no se puede instalar mediante pip y aparece en un archivo `requirements.txt`, toda la instalación da un error. En este caso, edite manualmente el archivo para excluir este paquete o para usar [opciones de pip](http://pip.readthedocs.org/en/latest/reference/pip_install.html#requirements-file-format) para hacer referencia a una versión instalable del paquete. Por ejemplo, puede ser preferible usar [`pip wheel`](http://pip.readthedocs.org/en/latest/reference/pip_wheel.html) para compilar una dependencia y agregar la opción `--find-links <path>` a su `requirements.txt`:

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

# <a name="search-paths"></a>Rutas de acceso de búsqueda

Con un uso típico de Python, la variable de entorno `PYTHONPATH` (o `IRONPYTHONPATH`, etc.) proporciona la ruta de acceso de búsqueda predeterminada para los archivos de módulo. Es decir, cuando se usa un instrucción `import <name>`, Python primero busca un nombre que coincida en sus módulos integrados, después busca en la carpeta que contiene el código Python que está ejecutando y, por último, busca en la "ruta de acceso de búsqueda de módulos" definida por la variable de entorno aplicable. (Consulte [The Module Search Path](https://docs.python.org/2/tutorial/modules.html#the-module-search-path) (Ruta de acceso de búsqueda de módulos) y [Environment variables](https://docs.python.org/2/using/cmdline.html#envvar-PYTHONPATH) (Variables de entorno) en la documentación principal de Python).

Sin embargo, Visual Studio omite la variable de entorno de ruta de acceso de búsqueda, aunque se haya establecido para todo el sistema. De hecho, se omite precisamente *porque* se establece para todo el sistema y, por consiguiente, surgen determinadas preguntas que no se pueden responder automáticamente: ¿Están los módulos a los que se hace referencia diseñados para Python 2.7 o Python 3.3? ¿Van a invalidar a los módulos de biblioteca estándar? ¿Es consciente el desarrollador de esto o se trata de un intento de secuestro de sesión malintencionado?

La compatibilidad de Python en Visual Studio proporciona un medio para especificar rutas de acceso de búsqueda directamente tanto en entornos como en proyectos. Estos se pasan como el valor de `PYTHONPATH` (o equivalente) al depurar o ejecutar la secuencia de comandos de Visual Studio. Mediante la incorporación de rutas de acceso de búsqueda, Visual Studio inspecciona las bibliotecas en estas ubicaciones y crea bases de datos de IntelliSense para ellas (esto puede tardar algún tiempo dependiendo del número de bibliotecas).

Para agregar una ruta de búsqueda, haga clic con el botón derecho en el elemento **Rutas de búsqueda** en el Explorador de soluciones, seleccione **Add Folder to Search Path…** (Agregar carpeta a ruta de acceso de búsqueda…) y seleccione la carpeta que desea incluir. Esta ruta de acceso se utiliza para cualquier entorno asociado al proyecto.

Los archivos con una extensión `.zip` o `.egg` también se pueden agregar como rutas de acceso de búsqueda seleccionando **Add Zip Archive to Search Path…** (Agregar archivo Zip a la ruta de acceso de búsqueda…). Al igual que con las carpetas, el contenido de estos archivos se examina y se pone a disposición de IntelliSense.

> [!Note]
> Es posible agregar una ruta de acceso de búsqueda a los módulos de Python 2.7 mientras utiliza Python 3.3 y es posible que vea errores en consecuencia.

Si utiliza periódicamente las mismas rutas de acceso de búsqueda y el contenido no cambia con frecuencia, puede ser más eficaz instalarlo en la carpeta de paquetes del sitio. A continuación, se analizará y almacenará en la base de datos de IntelliSense, siempre se asociará con el entorno deseado y no requerirá que se agregue una ruta de acceso de búsqueda para cada proyecto.

