---
title: Referencia de ventana Entornos de Python
description: Detalles de cada una de las pestañas que aparecen en la ventana Entornos de Python en Visual Studio.
ms.date: 03/18/2019
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: f08709c5231b2981db67900f47b49503269e948b
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545501"
---
# <a name="python-environments-window-tabs-reference"></a>Referencia de pestañas de la ventana Entorno de Python

Para abrir la ventana **Entornos de Python**:

- Seleccione el comando de menú **Vista** > **Otras ventanas** > **Entornos de Python**.
- Haga clic con el botón derecho en el nodo **Entornos de Python** de un proyecto en el **Explorador de soluciones** y seleccione **View All Python Environments** (Ver todos los entornos de Python).

Si expande la ventana **Entornos de Python** con un ancho suficiente, estas opciones se muestran como pestañas, lo cual puede resultarle más cómodo. Para mayor claridad, en este artículo las pestañas se muestran en la vista expandida.

::: moniker range="vs-2017"
![Vista de la ventana Python Environments (Entornos de Python) expandida](media/environments/environments-expanded-view.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Vista de la ventana Python Environments (Entornos de Python) expandida](media/environments/environments-expanded-view-2019.png)
::: moniker-end

## <a name="overview-tab"></a>Pestaña Información general

Proporciona información básica y comandos para el entorno:

::: moniker range="vs-2017"
![Ficha Información general de entornos de Python](media/environments/environments-overview-tab.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Ficha Información general de entornos de Python](media/environments/environments-overview-tab-2019.png)
::: moniker-end

| Comando | Descripción |
| --- | --- |
| **Hacer que este entorno sea el predeterminado para los proyectos nuevos** | Establece el entorno activo, que puede hacer que Visual Studio (2017, versión 15.5 y anteriores) deje de responder por unos instantes mientras se carga la base de datos de IntelliSense. Los entornos con muchos paquetes pueden dejar de responder durante más tiempo. |
| **Visitar el sitio web del distribuidor** | Abre un explorador en la URL proporcionada por la distribución de Python. Python 3.x, por ejemplo, se dirige a python.org. |
| **Abrir ventana interactiva** | Abre la [ventana interactiva (REPL)](python-interactive-repl-in-visual-studio.md) para este entorno en Visual Studio, aplicando cualquiera de los [scripts de inicio (ver a continuación)](#startup-scripts). |
| **Explorar scripts interactivos** | Vea [Scripts de inicio](#startup-scripts). |
| **Usar el modo interactivo de IPython** | Cuando se establece, se abre la ventana **interactiva** con IPython de manera predeterminada. Esto habilita los gráficos en línea, así como la sintaxis de IPython extendida como `name?` para ver la ayuda y `!command` para los comandos del shell. Esta opción se recomienda al usar una distribución de Anaconda, ya que necesita paquetes adicionales. Para obtener más información, vea [Uso de IPython en la ventana interactiva](interactive-repl-ipython.md). |
| **Abrir en PowerShell** | Inicie el intérprete en una ventana de comandos de PowerShell. |
| (Vínculos de carpeta y programa) | Le proporcionan acceso rápido a la carpeta de instalación del entorno, al intérprete *python.exe* y al intérprete *pythonw.exe*. La primera se abre en Explorador de Windows, los dos últimos abren una ventana de consola. |

### <a name="startup-scripts"></a>Scripts de inicio

A medida que usa las ventanas interactivas en su flujo de trabajo diario, probablemente desarrolle funciones del asistente que usa con frecuencia. Por ejemplo, puede crear una función que abra un DataFrame en Excel y, después, guardar ese código como un script de inicio de manera que siempre esté disponible en la ventana **interactiva**.

Los scripts de inicio contienen código que la ventana **interactiva** carga y ejecuta automáticamente, como importaciones, definiciones de función y literalmente cualquier otra cosa. Hay dos maneras de hacer referencia a dichos scripts:

1. Cuando instala un entorno, Visual Studio crea una carpeta *Documents\Visual Studio \<version>\Python Scripts\\\<environment>* donde &lt;versión&gt; se corresponde a la versión de Visual Studio (como 2017 o 2019) y &lt;entorno&gt; coincide con el nombre del entorno. Puede navegar fácilmente a la carpeta específica del entorno con el comando **Explorar scripts interactivos**. Cuando inicie la ventana **interactiva** para ese entorno, se cargan y ejecutan los archivos de *.py* que se encuentran aquí en orden alfabético.

1. El control **Scripts** de la pestaña **Herramientas** > **Opciones** > **Python** > **Ventanas interactivas** (consulte [Opciones de las ventanas interactivas](python-support-options-and-settings-in-visual-studio.md#interactive-windows-options)) pretende especificar una carpeta adicional para los scripts de inicio que se cargan y ejecutan en todos los entornos. No obstante, esta característica no funciona actualmente.

## <a name="configure-tab"></a>Pestaña Configurar

Si está disponible, la pestaña **Configurar** contiene detalles como se describe en la tabla siguiente. Si esta pestaña no está presente, significa que Visual Studio administra todos los detalles automáticamente.

::: moniker range="vs-2017"
![Pestaña Configuración de entornos de Python](media/environments/environments-configure-tab.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Pestaña Configuración de entornos de Python](media/environments/environments-configure-tab-2019.png)
::: moniker-end

| Campo | Descripción |
| --- | --- |
| **Descripción** | Nombre que se va a dar al entorno. |
| **Prefix path** (Ruta de acceso de prefijo) | Ubicación de la carpeta base del intérprete. Si rellena este valor y hace clic en **Detección automática**, Visual Studio intentará rellenar los demás campos automáticamente. |
| **Interpreter path** (Ruta de acceso del intérprete) | Ruta de acceso al ejecutable del intérprete, normalmente la ruta de acceso de prefijo seguida de **python.exe**. |
| **Windowed interpreter** (Intérprete en ventanas) | Ruta de acceso al ejecutable que no es de consola, normalmente la ruta de acceso de prefijo seguida de **pythonw.exe**. |
| **Library path** (Ruta de acceso a la biblioteca)<br/>(si está disponible) | Especifica la raíz de la biblioteca estándar, pero este valor se puede omitir si Visual Studio es capaz de solicitar una ruta de acceso más precisa desde el intérprete. |
| **Versión de lenguaje** | Se selecciona en el menú desplegable. |
| **Arquitectura** | Normalmente se detecta y rellena automáticamente; de lo contrario especifica **32** o **64 bits**. |
| **Path environment variable** (Variable de entorno de ruta de acceso) | Variable de entorno que el intérprete usa para encontrar rutas de acceso de búsqueda. Visual Studio cambia el valor de la variable al iniciar Python para que contenga las rutas de búsqueda del proyecto. Normalmente, esta propiedad se debe establecer en **PYTHONPATH**, pero algunos intérpretes utilizan un valor diferente. |

## <a name="packages-tab"></a>Pestaña Paquetes

*También se etiqueta como "pip" en versiones anteriores*

Administra los paquetes instalados en el entorno con pip (la pestaña **Paquetes (PyPI)** ) o conda (la pestaña **Paquetes (Conda)** para entornos en la versión 15.7 y posteriores de Visual Studio 2017). En esta pestaña también se pueden buscar e instalar paquetes nuevos, incluidas sus dependencias.

Los paquetes que ya están instalados aparecen con controles para actualizar (una flecha hacia arriba) y desinstalar (la X en un círculo) el paquete:

![Pestaña de los paquetes de los entornos de Python](media/environments/environments-pip-tab-controls.png)

Especifique los filtros de un término de búsqueda en la lista de paquetes instalados, así como paquetes que pueden instalarse desde PyPI.

::: moniker range="vs-2017"
![Pestaña de los paquetes de los entornos de Python con una búsqueda en "num"](media/environments/environments-pip-tab.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Pestaña de los paquetes de los entornos de Python con una búsqueda en "num"](media/environments/environments-pip-tab-2019.png)
::: moniker-end

Como puede ver en la imagen anterior, los resultados de la búsqueda muestran un número de paquetes que coinciden con el término de búsqueda; pero la primera entrada de la lista es un comando para ejecutar **pip install \<name>** directamente. Si se encuentra en la pestaña **Paquetes (Conda)** , en su lugar verá **conda install \<name>** :

::: moniker range="vs-2017"
![Pestaña de paquetes de Conda que muestra el comando conda install](media/environments/environments-conda-tab-install.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Pestaña de paquetes de Conda que muestra el comando conda install](media/environments/environments-conda-tab-install-2019.png)
::: moniker-end

En ambos casos, puede personalizar la instalación si agrega argumentos en el cuadro de búsqueda después del nombre del paquete. Cuando se incluyen argumentos, en los resultados de la búsqueda se muestra **pip install** o **conda install** seguido del contenido del cuadro de búsqueda:

::: moniker range="vs-2017"
![Uso de argumentos en comandos de instalación de pip y conda](media/environments/environments-pip-tab-arguments.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Uso de argumentos en comandos de instalación de pip y conda](media/environments/environments-pip-tab-arguments-2019.png)
::: moniker-end

Al instalar un paquete se crean subcarpetas dentro de la carpeta *Lib* del entorno en el sistema de archivos. Por ejemplo, si tiene instalado Python 3.6 en *c:\Python36*, los paquetes se instalan en *c:\Python36\Lib*; si tiene instalado Anaconda3 en *c:\Program Files\Anaconda3*, los paquetes se instalan en *c:\Program Files\Anaconda3\Lib*. En el caso de los entornos de Conda, los paquetes se instalan en la carpeta de ese entorno.

### <a name="grant-administrator-privileges-for-package-install"></a>Concesión de privilegios de administrador para la instalación de paquetes

Al instalar paquetes en un entorno que está situado en un área protegida del sistema de archivos, como *c:\Program Files\Anaconda3\Lib*, Visual Studio debe ejecutar `pip install` con permisos elevados para permitirle que cree subcarpetas del paquete. Cuando se necesita la elevación de privilegios, Visual Studio muestra el mensaje **Puede que se necesiten privilegios de administrador para instalar, actualizar o desinstalar paquetes para este entorno**:

![Mensaje de elevación de privilegios para la instalación del paquete](media/environments/environments-pip-elevate.png)

**Elevar ahora** concede privilegios administrativos a pip para una única operación, sujeto también a cualquier sistema operativo que solicite permisos. Al seleccionar **Continuar sin privilegios de administrador** se intenta instalar el paquete, pero pip produce un error al intentar crear carpetas con un resultado como **error: no se pudo crear "C:\Archivos de programa\Anaconda3\Lib\site-packages\png.py": permiso denegado.**

Al seleccionar **Elevar siempre al instalar o desinstalar paquetes** se impide que el cuadro de diálogo aparezca para el entorno en cuestión. Para que el cuadro de diálogo aparezca de nuevo, vaya a **Herramientas** > **Opciones** > **Python** > **General** y seleccione el botón **Restablecer todos los cuadros de diálogo ocultos de manera permanente**.

En esa misma pestaña de **opciones**, también puede seleccionar **Ejecutar siempre pip como administrador** para suprimir el cuadro de diálogo en todos los entornos. Vea [Opciones: pestaña General](python-support-options-and-settings-in-visual-studio.md#general-options).

### <a name="security-restrictions-with-older-versions-of-python"></a>Restricciones de seguridad con versiones anteriores de Python

Cuando se usa Python 2.6, 3.1 y 3.2, Visual Studio muestra la advertencia **Debido a restricciones de seguridad, la instalación desde Internet podría no funcionar en esta versión de Python**:

![Mensaje sobre las restricciones de pip install con una versión anterior de Python](media/environments/environments-old-version-restriction.png)

El motivo de la advertencia es que con estas versiones anteriores de Python, `pip install` no admite la Seguridad de la capa de transporte (TLS) 1.2, que es necesaria para descargar paquetes desde el proveedor, pypi.org. Las compilaciones de Python personalizadas pueden admitir TLS 1.2, en cuyo caso `pip install` podría funcionar.

Es posible descargar el *get-pip.py* apropiado para un paquete desde [bootstrap.pypa.io](https://bootstrap.pypa.io/), descargar manualmente un paquete desde [pypi.org](https://pypi.org/) y, a continuación, instalar el paquete desde esa copia local.

Pero lo recomendable es actualizar a Python 2.7 o 3.3+, en cuyo caso no aparece la advertencia.

::: moniker range="vs-2017"
## <a name="intellisense-tab"></a>Pestaña IntelliSense

Muestra el estado actual de la base de datos de finalización de IntelliSense:

![Pestaña IntelliSense de entornos de Python](media/environments/environments-intellisense-tab.png)

- En Visual Studio 2017, versión 15.5 y versiones anteriores, las finalizaciones de IntelliSense dependen de una base de datos que se han compilado para esa biblioteca. La creación de la base de datos se realiza en segundo plano cuando se instala una biblioteca, pero puede tardar un tiempo y es posible que no esté completa cuando comience a escribir código.
- Visual Studio 2017, versión 15.6 y posteriores, usa un método más rápido para proporcionar las finalizaciones que no dependen de la base de datos de forma predeterminada. Por esta razón la pestaña se etiqueta como **IntelliSense [base de datos deshabilitada]** . Puede habilitar la base de datos si desactiva la opción **Herramientas** > **Opciones** > **Python** > **Experimental** > **Usar el nuevo estilo IntelliSense para los entornos**.

Cuando Visual Studio detecta un nuevo entorno (o el usuario agrega uno), comienza a compilar automáticamente la base de datos analizando los archivos de origen de la biblioteca. Este proceso puede tardar desde un minuto a una hora o más dependiendo de lo que esté instalado. (Anaconda, por ejemplo, incluye muchas bibliotecas y tarda algún tiempo en compilar la base de datos.) Una vez finalizado, obtiene detalles de IntelliSense y no necesita actualizar la base de datos (con el botón **Refresh DB** (Actualizar base de datos)) hasta que instale más bibliotecas.

Las bibliotecas para las que no se han compilado los datos se marcan con **!** ; si la base de datos de un entorno no está completa, también aparece **!** junto a ella en la lista principal de entornos.

::: moniker-end

## <a name="see-also"></a>Vea también

- [Creación y administración de entornos de Python en Visual Studio](managing-python-environments-in-visual-studio.md)
- [Selección de un intérprete para un proyecto](selecting-a-python-environment-for-a-project.md)
- [Uso de requirements.txt para las dependencias](managing-required-packages-with-requirements-txt.md)
- [Rutas de acceso de búsqueda](search-paths.md)
