---
title: ¿Qué es la depuración?
description: Comprender lo que significa que depurar una aplicación
ms.custom: debug-experiments
ms.date: 10/17/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8f0aa6cbe09f902ef69e1fd5cb3a2d9712cabf28
ms.sourcegitcommit: d7f232a7596420e40ff8051d42cdf90203af4a74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2018
ms.locfileid: "52821453"
---
# <a name="what-is-debugging"></a>¿Qué es la depuración?

El depurador de Visual Studio es una herramienta eficaz. Antes de que se muestra cómo usarlo, queremos hablar sobre algunos de los términos como *depurador*, *depuración*, y *el modo de depuración*. De este modo, cuando hablamos más adelante encontrando y corrigiendo errores, hablaremos acerca de lo mismo.

## <a name="debugger-vs-debugging"></a>Depurador y depuración

El término *depuración* puede significar muchas cosas diferentes, pero más literalmente, implica la eliminación de los errores desde el código. Ahora, hay muchas maneras de hacerlo. Por ejemplo, puede depurar examinando el código busca errores tipográficos o mediante el uso de un analizador de código. Puede depurar el código mediante el uso de un generador de perfiles de rendimiento. O bien, se puede depurar utilizando un *depurador*.

Un depurador es una herramienta muy especializada de desarrollador que se adjunta a la aplicación en ejecución y le permite inspeccionar el código. En la documentación de depuración para Visual Studio, esto normalmente es lo que queremos decir cuando hablamos de "depuración".

## <a name="debug-mode-vs-running-your-app"></a>Depurar en modo frente al ejecutar la aplicación

Al ejecutar la aplicación en Visual Studio por primera vez, puede iniciarlo presionando el botón de flecha verde ![Iniciar depuración](../debugger/media/dbg-tour-start-debugging.png "Iniciar depuración") en la barra de herramientas (o **F5**). De forma predeterminada, el **depurar** valor aparece en la lista desplegable a la izquierda. Si está familiarizado con Visual Studio, esto puede dejar la impresión que depurar la aplicación tiene algo que ver con la ejecución de la aplicación--qué empresarial estratégico, pero estos son fundamentalmente de dos tareas muy diferentes.

![Seleccione una compilación de depuración](../debugger/media/what-is-debugging-debug-build.png)

Un **depurar** valor indica una configuración de depuración. Al iniciar la aplicación (presione la flecha verde o **F5**) en una configuración de depuración, iniciar la aplicación en *el modo de depuración*, lo que significa que está ejecutando la aplicación con un depurador adjunto. Esto permite un conjunto completo de características que puede usar para ayudar a detectar errores en la aplicación de depuración.

Si tiene abierto un proyecto, elija el selector de lista desplegable, donde dice **depurar** y elija **versión** en su lugar.

![Seleccione una versión de lanzamiento](../debugger/media/what-is-debugging-release-build.png)

Al cambiar esta configuración, cambie el proyecto desde una configuración de depuración a la configuración release. Los proyectos de Visual Studio tienen configuraciones independientes para el lanzamiento y la depuración del programa. Compile la versión de depuración para la depuración y la versión de lanzamiento para la distribución de la versión final. Una compilación de versión está optimizada para rendimiento, pero es mejor para la depuración de una compilación de depuración.

## <a name="when-to-use-a-debugger"></a>Cuándo usar un depurador

El depurador es una herramienta esencial para encontrar y corregir errores en las aplicaciones. Sin embargo, contexto es el rey, y es importante aprovechar todas las herramientas a su objeto descartable que le ayudarán a eliminar rápidamente los errores. A veces, el derecho "tool" podría ser una práctica de codificación mejores. Al aprender cuándo se debe usar al depurador frente a alguna otra herramienta, también obtendrá información sobre cómo usar al depurador de forma más eficaz. Si ya sabe que necesita obtener información sobre el depurador, vea [de depuración para principiantes absolutos](../debugger/debugging-absolute-beginners.md). En caso contrario, siga el vínculo de **pasos siguientes**.

## <a name="next-steps"></a>Pasos siguientes

En este artículo, ha aprendido algunos conceptos generales de depuración. A continuación, puede empezar a aprender cómo depurar con Visual Studio y cómo escribir código con menos errores. El siguiente artículo se muestra C# ejemplos de código, pero los conceptos se aplican a todos los idiomas compatibles con Visual Studio.

> [!div class="nextstepaction"]
> [Corrección de errores escribiendo mejor código de C#](../debugger/write-better-code-with-visual-studio.md)
