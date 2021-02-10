---
title: ¿Qué es la depuración?
description: Comprenda lo que significa depurar una aplicación.
ms.custom: debug-experiment
ms.date: 10/17/2018
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3435b7a270d89dc38f5ff10a1350418a24f91c0a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883940"
---
# <a name="what-is-debugging"></a>¿Qué es la depuración?

El depurador de Visual Studio es una herramienta eficaz. Antes de mostrar cómo se usa, queremos hablar sobre algunos términos, como *depurador*, *depuración* y *modo de depuración*. De este modo, cuando hablemos más adelante sobre cómo encontrar y corregir errores, estaremos hablando de lo mismo.

## <a name="debugger-vs-debugging"></a>Depurador frente a depuración

El término *depuración* puede significar una gran cantidad de cosas diferentes, pero literalmente significa quitar errores del código. Sin embargo, hay muchas formas de hacerlo. Por ejemplo, puede examinar el código en busca de errores tipográficos o usar un analizador de código. También podría depurar el código mediante un generador de perfiles de rendimiento. O bien, puede usar un *depurador*.

Un depurador es una herramienta de desarrollo muy especializada que se asocia a la aplicación en ejecución y permite inspeccionar el código. En la documentación de depuración de Visual Studio, esto es normalmente de lo que hablamos cuando decimos "depuración".

## <a name="debug-mode-vs-running-your-app"></a>Modo de depuración frente a ejecución de la aplicación

Al ejecutar la aplicación en Visual Studio por primera vez, puede iniciarla presionando el botón de flecha verde ![Iniciar depuración](../debugger/media/dbg-tour-start-debugging.png "Iniciar depuración") en la barra de herramientas (o **F5**). De forma predeterminada, el valor **Depurar** aparece en la lista desplegable de la izquierda. Si no está familiarizado con Visual Studio, puede que parezca que la depuración de la aplicación tiene algo que ver con su ejecución, lo cual, aunque es cierto, estas son dos tareas básicamente muy diferentes.

![Selección de una compilación de depuración](../debugger/media/what-is-debugging-debug-build.png)

Un valor de **Depurar** indica una configuración de depuración. Al iniciar la aplicación (presionar la flecha verde o **F5**) en una configuración de depuración, se inicia la aplicación en *modo de depuración*, lo que significa que está ejecutando la aplicación con un depurador asociado. Esta asociación permite un conjunto completo de características de depuración que puede usar para buscar errores en la aplicación.

Si tiene un proyecto abierto, elija el selector desplegable donde pone **Depurar** y elija en su lugar **Versión**.

![Selección de una compilación de versión](../debugger/media/what-is-debugging-release-build.png)

Al cambiar esta configuración, se cambia el proyecto de una configuración de depuración a una configuración de versión. Los proyectos de Visual Studio tienen configuraciones independientes para el lanzamiento y la depuración del programa. La versión de depuración se compila para la depuración y la versión de lanzamiento para la distribución final. Una compilación de versión está optimizada para el rendimiento, pero una compilación de depuración es mejor para la depuración.

## <a name="when-to-use-a-debugger"></a>Cuándo usar un depurador

El depurador es una herramienta esencial para buscar y corregir errores en las aplicaciones. Sin embargo, el contexto es clave, y es importante aprovechar todas las herramientas de que disponga para ayudarle a eliminar rápidamente errores. A veces, la "herramienta" adecuada puede ser un procedimiento de creación de código mejor. Si aprende a usar el depurador frente en lugar de alguna otra herramienta, también aprenderá a usar el depurador de forma más eficaz.

## <a name="next-steps"></a>Pasos siguientes

En este artículo, ha aprendido algunos conceptos generales de depuración. Después, puede empezar a aprender a depurar con Visual Studio y a escribir código con menos errores. En los artículos siguientes se muestran ejemplos de código de C#, pero los conceptos se aplican a todos los lenguajes compatibles con Visual Studio.

> [!div class="nextstepaction"]
> [Depuración para principiantes sin experiencia](../debugger/debugging-absolute-beginners.md)

> [!div class="nextstepaction"]
> [Herramientas y técnicas de depuración](../debugger/write-better-code-with-visual-studio.md)
