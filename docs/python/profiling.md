---
title: "Medición del rendimiento de código Python en Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 7/13/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2723d4d0-89c8-4279-bfc2-27c0834a997e
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6d25db4639f2c8391c1e32542701ea359f560178
ms.openlocfilehash: f01c42f073859e2e609123eb67cc9df8e26cef75
ms.contentlocale: es-es
ms.lasthandoff: 07/18/2017

---

# <a name="profiling-python-code"></a>Generación de perfiles del código Python

Visual Studio admite la generación de perfiles de una aplicación Python cuando se usan intérpretes basados en CPython.

La generación de perfiles se inicia a través del comando de menú **Analizar > Launch Python Profiling (Iniciar generación de perfiles de Python)**, que abre un cuadro de diálogo de configuración:

![Cuadro de diálogo de configuración de generación de perfiles](media/profiling-start.png)

Al seleccionar **Aceptar**, el generador de perfiles se ejecuta y abre un informe de rendimiento a través del cual puede explorar cómo se emplea el tiempo en la aplicación:

![Informe de rendimiento de generación de perfiles](media/profiling-results.png)

Para información general, consulte lo siguiente:

Para una demostración del tutorial, consulte el vídeo (8 minutos y 52 segundos) [Profiling with Python Tools for Visual Studio](http://www.youtube.com/watch?v=K-KqkFkp55k) (Generación de perfiles con Herramientas de Python para Visual Studio).

> [!VIDEO https://www.youtube.com/embed/K-KqkFkp55k]

## <a name="profiling-for-ironpython"></a>Generación de perfiles para IronPython

Dado que IronPython no es un intérprete basado en CPython, la característica de generación de perfiles anterior no funciona.

En su lugar, utilice el generador de perfiles de Visual Studio. NET iniciando `ipy.exe` directamente como la aplicación de destino y usando los argumentos apropiados para iniciar el script de inicio. Incluya `-X:Debug` en la línea de comandos para exigir que todo el código Python se pueda depurar y permita la generación de perfiles. Este argumento genera un informe de rendimiento que incluye el tiempo invertido tanto en el runtime de IronPython como en el código. El código se identifica con nombres alterados.

Como alternativa, IronPython tiene algunas de sus propias características de generación de perfiles integradas, pero actualmente no hay un buen visualizador para ellas. Consulte [An IronPython Profiler](http://blogs.msdn.com/b/curth/archive/2009/03/29/an-ironpython-profiler.aspx) (Un generador de perfiles de Python) (blogs de MSDN) para saber lo que está disponible.
