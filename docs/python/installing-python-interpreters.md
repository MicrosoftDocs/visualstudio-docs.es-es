---
title: Selección e instalación de los intérpretes de Python
description: Una lista completa de los intérpretes de Python compatibles con Visual Studio, con instrucciones breves sobre dónde encontrar sus instaladores.
ms.date: 10/09/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 3a81d81160bd6ad097e848f4af964d6ed00b17a5
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2018
ms.locfileid: "51348713"
---
# <a name="install-python-interpreters"></a>Instalación de intérpretes de Python

De forma predeterminada, la instalación de la carga de trabajo de desarrollo de Python en Visual Studio de 2017 también instala Python 3 (64 bits). Puede optar por instalar las versiones de 32 bits y 64 bits de Python 2, Python 3, Anaconda 2 y Anaconda 3, como se describe en [Instalación](installing-python-support-in-visual-studio.md).

También puede instalar manualmente cualquiera de los intérpretes que aparecen en la tabla siguiente fuera del Instalador de Visual Studio. Por ejemplo, si instaló Anaconda 3 antes de instalar Visual Studio, no necesita volver a instalarlo mediante el instalador de Visual Studio. También puede instalar un intérprete manualmente si, por ejemplo, hay una versión más reciente disponible que todavía no aparece en el instalador de Visual Studio.

Para **Visual Studio 2015 y versiones anteriores**, debe instalar manualmente uno de los intérpretes.

Visual Studio (todas las versiones) detecta automáticamente cada intérprete de Python instalado y su entorno mediante la comprobación del registro de acuerdo con [PEP 514 - Python registration in the Windows registry](https://www.python.org/dev/peps/pep-0514/) (PEP 514: registro de Python en el Registro de Windows). Las instalaciones de Python se encuentran normalmente en **HKEY_LOCAL_MACHINE\SOFTWARE\Python** (32 bits) y **HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Python** (64 bits) y, luego, dentro de los nodos para la distribución, como **PythonCore** (CPython) y **ContinuumAnalytics** (Anaconda).

Si Visual Studio no detecta un entorno instalado, consulte [Identificación manual de un entorno existente](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment).

Visual Studio muestra todos los entornos conocidos en la ventana [**Entornos de Python**](managing-python-environments-in-visual-studio.md#the-python-environments-window) y detecta automáticamente las actualizaciones de los intérpretes existentes.

| Intérprete | Descripción |
| --- | --- |
| [CPython](https://www.python.org/) | Intérprete "nativo" y que se usa con más frecuencia, disponible en versiones de 32 y 64 bits (se recomienda la versión de 32 bits). Incluye características más recientes del lenguaje, máxima compatibilidad con paquetes de Python, compatibilidad completa con la depuración e interoperabilidad con [IPython](http://ipython.org/). Consulte también: [Should I use Python 2 or Python 3? (¿Debo usar Python 2 o Python 3?)](https://wiki,python.org/moin/Python2orPython3). Tenga en cuenta que Visual Studio 2015 y versiones anteriores no admiten Python 3.6 y pueden generar errores de tipo **Versión 3.6 de Python no compatible**. Use la versión Python 3.5 o anteriores. |
| [IronPython](https://github.com/IronLanguages/ironpython2) | Implementación de .NET de Python, disponible en versiones de 32 y 64 bits, que proporciona interoperabilidad con C#, F# y Visual Basic, acceso a las API de .NET, depuración estándar de Python (pero no depuración en modo mixto de C++) y depuración mixta de IronPython y C#. IronPython, sin embargo, no admite entornos virtuales. |
| [Anaconda](https://www.continuum.io) | Plataforma de ciencia de datos abierta con tecnología de Python que incluye la versión más reciente de CPython y la mayoría de los paquetes de difícil instalación. Es la opción recomendable si no puede decidirse. |
| [PyPy](https://www.pypy.org/) | Implementación JIT de seguimiento de alto rendimiento de Python adecuada para programas de ejecución prolongada y situaciones donde se identifican problemas de rendimiento pero no puede encontrar otras resoluciones. Funciona con Visual Studio, pero con compatibilidad limitada para características de depuración avanzadas. |
| [Jython](http://www.jython.org/) | Implementación de Python en la Máquina virtual Java (JVM). Es similar a IronPython, donde el código que se ejecuta en Jython puede interactuar con clases y bibliotecas de Java, pero no es posible que no pueda utilizar muchas bibliotecas pensadas para CPython. Funciona con Visual Studio, pero con compatibilidad limitada para características de depuración avanzadas. |

Los desarrolladores que desean proporcionar nuevas formas de detección para entornos de Python pueden consultar [PTVS Environment Detection](https://github.com/Microsoft/PTVS/wiki/Extensibility-Environments) (Entorno detección PTVS) en github.com.

## <a name="move-an-interpreter"></a>Trasladar un intérprete

Si mueve un intérprete existente a una ubicación nueva con el sistema de archivos, Visual Studio no detecta automáticamente el cambio.

- Si originalmente ha especificado la ubicación del intérprete a través de la ventana **Entornos de Python**, edite su entorno con la pestaña **Configurar** de esa ventana para identificar la ubicación nueva. Vea [Identificación manual de un entorno existente](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment).

- Si instaló el intérprete con un programa de instalación, use los pasos siguientes para volver a instalar el intérprete en la ubicación nueva:

  1. Restaure el intérprete de Python a su ubicación original.
  2. Desinstale el intérprete mediante el instalador, que borra las entradas del Registro.
  3. Vuelva a instalar el intérprete en la ubicación deseada.
  4. Reinicie Visual Studio, el que debería detectar automáticamente la ubicación nueva en lugar de la antigua.

Al seguir este proceso, se asegura de que las entradas del Registro que identifican la ubicación del intérprete, que Visual Studio usa, se actualizan correctamente. Usar un instalador también controla cualquier otro efecto secundario que pudiera surgir.

## <a name="see-also"></a>Vea también

- [Administración de entornos de Python](managing-python-environments-in-visual-studio.md)
- [Selección de un intérprete para un proyecto](selecting-a-python-environment-for-a-project.md)
- [Uso de requirements.txt para las dependencias](managing-required-packages-with-requirements-txt.md)
- [Rutas de acceso de búsqueda](search-paths.md)
- [Referencia de ventana Entornos de Python](python-environments-window-tab-reference.md)
