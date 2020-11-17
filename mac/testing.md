---
title: Herramientas de prueba de Visual Studio para Mac
description: Creación y ejecución de pruebas con Visual Studio para Mac.
ms.date: 11/09/2020
ms.topic: conceptual
helpviewer_keywords:
- testing tools [Visual Studio for Mac]
- unit tests [Visual Studio for Mac]
ms.author: jomatthi
author: jmatthiesen
ms.openlocfilehash: 3956c3158fd4ec1ad32b76882ac3f9d4cf1ea9bf
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493392"
---
# <a name="testing-tools-in-visual-studio-for-mac"></a>Herramientas de prueba de Visual Studio para Mac

Las herramientas de prueba de Visual Studio para Mac pueden ayudarle a usted y a su equipo a desarrollar y mantener altos estándares de excelencia de código. Las pruebas unitarias se pueden escribir y ejecutar mediante el marco de pruebas unitarias de Microsoft (MSTest), xUnit o NUnit.

## <a name="creating-tests"></a>Crear pruebas
Para empezar a trabajar con las pruebas, puede crear un nuevo proyecto de prueba en la solución. Para ello, haga clic con el botón derecho en la solución y elija el menú **Agregar > Nuevo proyecto...** . Después, elija una de las categorías de pruebas en el lado izquierdo del cuadro de diálogo (por ejemplo, la categoría **Web y consola > Pruebas**). Seleccione el tipo de proyecto de prueba que quiere crear y luego haga clic en Siguiente. Siga las instrucciones de los cuadros de diálogo que aparecen y, después, se agregará un nuevo proyecto de prueba a la solución.

![Cuadro de diálogo Nuevo proyecto con la sección Web y consola > Pruebas seleccionada, que muestra los proyectos xUnit, MSTest y NUnit](media/create-new-test-project.PNG)

> [!NOTE]
> Para más información sobre las pruebas unitarias de las aplicaciones de .NET Core y cómo seleccionar marcos de pruebas unitarias, vea [Pruebas unitarias en .NET Core y .NET Standard](/dotnet/core/testing/?pivots=xunit).

## <a name="running-tests"></a>Ejecución de las pruebas
La ventana **Pruebas unitarias** se usa para ejecutar pruebas unitarias y se abre mediante el menú **Ver > Pruebas**. Las pruebas unitarias de la solución se detectan automáticamente y se muestran en esta ventana, donde puede ejecutar todas las pruebas o un conjunto de las que haya seleccionado.

![Ventana de prueba que muestra una lista de pruebas unitarias y una barra de herramientas para ejecutar o detener pruebas.](media/test-window.PNG)

Al editar una clase de C# que contiene pruebas unitarias, para ejecutar las pruebas haga clic con el botón derecho en la clase de prueba o en un método de prueba y elija el menú **Ejecutar pruebas** o **Depurar pruebas**. Al elegir el elemento de menú **Ejecutar pruebas**, se ejecutarán las pruebas en la ventana de prueba; y al elegir el menú **Depurar pruebas**, ocurrirá lo mismo y se asociará el depurador para que pueda solucionar problemas en el código.

![Menú contextual del editor con las opciones Ejecutar y Depurar pruebas](media/run-tests-context-menu.PNG)

Mientras se ejecutan las pruebas, aparece una ventana **Resultados de pruebas** para revisar las pruebas que se han realizado correctamente o con errores, y el resultado de la ejecución de esas pruebas.

![Ventana Resultados de la prueba que muestra una prueba con errores y un recuento de 21 pruebas realizadas correctamente y 1 prueba con errores.](media/test-results-window.PNG)

## <a name="see-also"></a>Consulte también

- [Pruebas unitarias en .NET Core y .NET Standard](/dotnet/core/testing)
- [Introducción a las pruebas unitarias (Visual Studio en Windows)](/visualstudio/test/getting-started-with-unit-testing)
- [Conceptos básicos de las pruebas unitarias (Visual Studio en Windows)](/visualstudio/test/unit-test-basics)