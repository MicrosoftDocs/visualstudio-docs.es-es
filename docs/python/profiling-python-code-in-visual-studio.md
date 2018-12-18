---
title: Medición del rendimiento del código de Python
description: Describe cómo usar el generador de perfiles de Visual Studio para comprobar el rendimiento del código de Python al usar intérpretes basados en CPython.
ms.date: 11/12/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 0b5ca29b061f0ba61eec775a0344fb8d2067e08d
ms.sourcegitcommit: 6a955a2d179cd0e137942389f940d9fcbbe125de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/13/2018
ms.locfileid: "51607489"
---
# <a name="profile-python-code"></a>Generación de perfiles de código de Python

Puede generar perfiles de una aplicación de Python al usar intérpretes de CPython (vea [Generación de perfiles de la matriz de características](overview-of-python-tools-for-visual-studio.md#matrix-profiling) para conocer la disponibilidad de esta característica en las distintas versiones de Visual Studio).

## <a name="profiling-for-cpython-based-interpreters"></a>Generación de perfiles para intérpretes basados en CPython

La generación de perfiles se inicia a través del comando de menú **Analizar** > **Launch Python Profiling** (Iniciar generación de perfiles de Python), que abre un cuadro de diálogo de configuración:

![Cuadro de diálogo de configuración de generación de perfiles](media/profiling-start.png)

Al seleccionar **Aceptar**, el generador de perfiles se ejecuta y abre un informe de rendimiento a través del cual puede explorar cómo se emplea el tiempo en la aplicación:

![Informe de rendimiento de generación de perfiles](media/profiling-results.png)

|   |   |
|---|---|
| ![icono de cámara de película para vídeo](../install/media/video-icon.png "Ver un vídeo") | [Eche un vistazo a un vídeo (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Profiling-Python-s6FoC6LWE_1005918567) para ver una demostración de la generación de perfiles de Python (3 m 00 s).|

> [!Note]
> En la actualidad, Visual Studio solo admite este nivel de generación de perfiles para toda la aplicación, pero sí desea sus comentarios sobre las funcionalidades futuras. Use el botón [**Comentarios sobre el producto**](#feedback) en la parte inferior de esta página.

## <a name="profiling-for-ironpython"></a>Generación de perfiles para IronPython

Dado que IronPython no es un intérprete basado en CPython, la característica de generación de perfiles anterior no funciona.

En su lugar, utilice el generador de perfiles de Visual Studio. NET iniciando *ipy.exe* directamente como la aplicación de destino y usando los argumentos apropiados para iniciar el script de inicio. Incluya `-X:Debug` en la línea de comandos para asegurarse de que todo el código Python se pueda depurar y permita la generación de perfiles. Este argumento genera un informe de rendimiento que incluye el tiempo invertido tanto en el runtime de IronPython como en el código. El código se identifica con nombres alterados.

Como alternativa, IronPython tiene algunas de sus propias características de generación de perfiles integradas, pero actualmente no hay un buen visualizador para ellas. Consulte [An IronPython Profiler](https://blogs.msdn.microsoft.com/curth/2009/03/30/an-ironpython-profiler/) (Un generador de perfiles de Python) (blogs de MSDN) para saber lo que está disponible.
