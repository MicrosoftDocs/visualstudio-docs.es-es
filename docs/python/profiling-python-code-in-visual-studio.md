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
ms.openlocfilehash: 6e6a37301477b43063169143456fc21a3c783968
ms.sourcegitcommit: 4976419fae731860295dbcd072e6778832f7255d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/06/2021
ms.locfileid: "97917916"
---
# <a name="profile-python-code"></a>Generación de perfiles de código de Python

Puede generar perfiles de una aplicación de Python al usar intérpretes de CPython (vea [Generación de perfiles de la matriz de características](overview-of-python-tools-for-visual-studio.md#matrix-profiling) para conocer la disponibilidad de esta característica en las distintas versiones de Visual Studio).

## <a name="profiling-for-cpython-based-interpreters"></a>Generación de perfiles para intérpretes basados en CPython

La generación de perfiles se inicia a través del comando de menú **Depurar** > **Iniciar la generación de perfiles de Python**, que abre un cuadro de diálogo de configuración:

![Cuadro de diálogo de configuración de generación de perfiles](media/profiling-start.png)

Al seleccionar **Aceptar**, el generador de perfiles se ejecuta y abre un informe de rendimiento a través del cual puede explorar cómo se emplea el tiempo en la aplicación:

![Informe de rendimiento de generación de perfiles](media/profiling-results.png)

> [!Note]
> Al generar perfiles de una aplicación de Python, Visual Studio recopila datos durante la vigencia del proceso. Actualmente no es posible pausar la generación de perfiles. Nos encantaría recibir sus comentarios sobre las funcionalidades futuras. Use el botón **Comentarios sobre el producto** que está en la parte inferior de esta página.

## <a name="profiling-for-ironpython"></a>Generación de perfiles para IronPython

Dado que IronPython no es un intérprete basado en CPython, la característica de generación de perfiles anterior no funciona.

En su lugar, utilice el generador de perfiles de Visual Studio. NET iniciando *ipy.exe* directamente como la aplicación de destino y usando los argumentos apropiados para iniciar el script de inicio. Incluya `-X:Debug` en la línea de comandos para asegurarse de que todo el código Python se pueda depurar y permita la generación de perfiles. Este argumento genera un informe de rendimiento que incluye el tiempo invertido tanto en el runtime de IronPython como en el código. El código se identifica con nombres alterados.

Como alternativa, IronPython tiene algunas de sus propias características de generación de perfiles integradas, pero actualmente no hay un buen visualizador para ellas. Consulte [An IronPython Profiler](/archive/blogs/curth/an-ironpython-profiler) (Un generador de perfiles de Python) (blogs de MSDN) para saber lo que está disponible.