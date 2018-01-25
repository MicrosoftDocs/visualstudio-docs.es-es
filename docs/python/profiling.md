---
title: "Medición del rendimiento de código Python en Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 01/09/2018
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: bdfd378a9441aba9c57c56f1f853e5cdd27a8d49
ms.sourcegitcommit: 11740fed01cc602252ef698aaa11c07987b00570
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/12/2018
---
# <a name="profiling-python-code"></a>Generación de perfiles de código de Python

Visual Studio admite la generación de perfiles de una aplicación Python cuando se usan intérpretes basados en CPython.

La generación de perfiles se inicia a través del comando de menú **Analizar > Launch Python Profiling (Iniciar generación de perfiles de Python)**, que abre un cuadro de diálogo de configuración:

![Cuadro de diálogo de configuración de generación de perfiles](media/profiling-start.png)

Al seleccionar **Aceptar**, el generador de perfiles se ejecuta y abre un informe de rendimiento a través del cual puede explorar cómo se emplea el tiempo en la aplicación:

![Informe de rendimiento de generación de perfiles](media/profiling-results.png)

Si quiere ver una demo, eche un vistazo al vídeo [Profiling Python](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=s6FoC6LWE_1005918567) (Generación de perfiles de Python) de Microsoft Virtual Academy (3 minutos).

> [!VIDEO https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Profiling-Python-s6FoC6LWE_1005918567]

## <a name="profiling-for-ironpython"></a>Generación de perfiles para IronPython

Dado que IronPython no es un intérprete basado en CPython, la característica de generación de perfiles anterior no funciona.

En su lugar, utilice el generador de perfiles de Visual Studio. NET iniciando `ipy.exe` directamente como la aplicación de destino y usando los argumentos apropiados para iniciar el script de inicio. Incluya `-X:Debug` en la línea de comandos para asegurarse de que todo el código Python se pueda depurar y permita la generación de perfiles. Este argumento genera un informe de rendimiento que incluye el tiempo invertido tanto en el runtime de IronPython como en el código. El código se identifica con nombres alterados.

Como alternativa, IronPython tiene algunas de sus propias características de generación de perfiles integradas, pero actualmente no hay un buen visualizador para ellas. Consulte [An IronPython Profiler](http://blogs.msdn.com/b/curth/archive/2009/03/29/an-ironpython-profiler.aspx) (Un generador de perfiles de Python) (blogs de MSDN) para saber lo que está disponible.