---
title: "Medición del rendimiento de código Python en Visual Studio | Microsoft Docs"
description: "Describe cómo usar el generador de perfiles de Visual Studio para comprobar el rendimiento del código de Python al usar intérpretes basados en CPython."
ms.custom: 
ms.date: 01/09/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: 
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 4b6b2be69cc0d52774c0fc5c8cd7f3b60273fd02
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="profiling-python-code"></a>Generación de perfiles de código de Python

Puede generar perfiles de una aplicación de Python al usar intérpretes de CPython (vea [Generación de perfiles de la matriz de características](overview-of-python-tools-for-visual-studio.md#matrix-profiling) para conocer la disponibilidad de esta característica en las distintas versiones de Visual Studio).

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