---
title: Medición del rendimiento del código de Python
description: Use el generador de perfiles de Visual Studio para comprobar el rendimiento del código de Python al usar intérpretes basados en CPython.
ms.date: 11/12/2018
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: b47b59c8d45d76fae1e61584510ae39fe5a91784
ms.sourcegitcommit: 5027eb5c95e1d2da6d08d208fd6883819ef52d05
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2020
ms.locfileid: "94973801"
---
# <a name="profile-python-code"></a>Generación de perfiles de código de Python

Puede generar perfiles de una aplicación de Python al usar intérpretes de CPython (vea [Generación de perfiles de la matriz de características](overview-of-python-tools-for-visual-studio.md#matrix-profiling) para conocer la disponibilidad de esta característica en las distintas versiones de Visual Studio).

## <a name="profiling-for-cpython-based-interpreters"></a>Generación de perfiles para intérpretes basados en CPython

La generación de perfiles se inicia a través del comando de menú **Depurar** > **Iniciar la generación de perfiles de Python**, que abre un cuadro de diálogo de configuración:

![Cuadro de diálogo de configuración de generación de perfiles](media/profiling-start.png)

Al seleccionar **Aceptar**, el generador de perfiles se ejecuta y abre un informe de rendimiento a través del cual puede explorar cómo se emplea el tiempo en la aplicación:

![Informe de rendimiento de generación de perfiles](media/profiling-results.png)

> [!Note]
> En la actualidad, Visual Studio solo admite este nivel de generación de perfiles para toda la aplicación, pero sí desea sus comentarios sobre las funcionalidades futuras. Use el botón **Comentarios sobre el producto** que está en la parte inferior de esta página.

## <a name="profiling-for-ironpython"></a>Generación de perfiles para IronPython

Dado que IronPython no es un intérprete basado en CPython, la característica de generación de perfiles anterior no funciona.

En su lugar, utilice el generador de perfiles de Visual Studio. NET iniciando *ipy.exe* directamente como la aplicación de destino y usando los argumentos apropiados para iniciar el script de inicio. Incluya `-X:Debug` en la línea de comandos para asegurarse de que todo el código Python se pueda depurar y permita la generación de perfiles. Este argumento genera un informe de rendimiento que incluye el tiempo invertido tanto en el runtime de IronPython como en el código. El código se identifica con nombres alterados.

Como alternativa, IronPython tiene algunas de sus propias características de generación de perfiles integradas, pero actualmente no hay un buen visualizador para ellas. Consulte [An IronPython Profiler](/archive/blogs/curth/an-ironpython-profiler) (Un generador de perfiles de Python) (blogs de MSDN) para saber lo que está disponible.