---
title: Introducción a las pruebas unitarias
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- unit testing, create unit test plans
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: df48a659d7718691d86909458a4a1a150d2d64dd
ms.sourcegitcommit: 87d7123c09812534b7b08743de4d11d6433eaa13
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/01/2019
ms.locfileid: "57223525"
---
# <a name="get-started-with-unit-testing"></a>Introducción a las pruebas unitarias

Use Visual Studio para definir y ejecutar pruebas unitarias para conservar el estado del código, garantizar la cobertura del código y detectar errores y fallos antes de que lo hagan los clientes. Ejecute las pruebas unitarias con frecuencia para asegurarse de que el código funciona correctamente.

## <a name="create-unit-tests"></a>Crear pruebas unitarias

En esta sección se describe de forma general cómo se crea un proyecto de prueba unitaria.

> [!TIP]
> El proyecto que se va a probar, "Hola mundo", es un proyecto de ejemplo y no se mostrará código relacionado con él. Si quiere crear un proyecto "Hola mundo" para probarlo, vea [Uso de Visual Studio para crear la primera aplicación de consola de C#](../ide/quickstart-csharp-console.md). Para obtener un artículo con un tutorial completo, vea [Crear y ejecutar pruebas unitarias en código administrado](walkthrough-creating-and-running-unit-tests-for-managed-code.md).

1. Cree un proyecto de prueba unitaria.

   ![Agregar un proyecto de prueba unitaria a la solución](media/createunittest1.png)

1. Dé un nombre al proyecto.

   ![Plantilla de proyecto de prueba unitaria](media/createunittest2.png)

   El proyecto se agrega a la solución.

   ![Proyecto de prueba unitaria en el Explorador de soluciones](media/createunittest5.png)

1. En el proyecto de prueba unitaria, agregue una referencia al proyecto que quiere probar.

   ![Agregar una referencia al proyecto de prueba unitaria](media/createunittest6.png)

1. Seleccione el proyecto que contiene el código que va a probar.

   ![Seleccionar la referencia que se va a agregar](media/createunittest7.png)

1. Codifique la prueba unitaria.

   ![Agregar código a la prueba unitaria](media/createunittest8.png)

También puede crear códigos auxiliares de método de pruebas unitarias con el **comando** [Crear pruebas unitarias](create-unit-tests-menu.md).

![Usar el comando Crear pruebas unitarias](media/createunittestcommand2.png)

## <a name="run-unit-tests"></a>Ejecutar pruebas unitarias

1. Abra el **Explorador de pruebas**.

   ![En el menú Prueba, abra el Explorador de pruebas.](media/rununittest1.png)

1. Ejecute las pruebas unitarias.

   ![Ejecutar pruebas unitarias en el Explorador de pruebas](media/rununittest2.png)

   Puede ver las pruebas unitarias que se han superado o han dado error en el **Explorador de pruebas**.

   ![Revisar los resultados de pruebas unitarias en el Explorador de pruebas](media/rununittest3.png)

## <a name="view-live-unit-test-results"></a>Ver los resultados de las pruebas unitarias en vivo

Si está usando el marco de pruebas de MSTest, xUnit o NUnit en Visual Studio 2017 o versiones posteriores, puede ver los resultados en vivo de sus pruebas unitarias.

> [!NOTE]
> Live Unit Testing solo está disponible en Visual Studio Enterprise Edition.

1. Active las pruebas unitarias en vivo desde el menú **Prueba**.

   ![Activar las pruebas unitarias en vivo](media/live-test-results-start.png)

1. Vea los resultados de las pruebas dentro de la ventana del editor de código a medida que escribe y edita el código.

   ![Ver los resultados de las pruebas](media/live-test-results-ui.png)

1. Seleccione los indicadores de resultados de la prueba para ver más información.

   ![Seleccionar los indicadores de resultados de la prueba](media/live-test-results-details.png)

Para obtener más información, vea [Live Unit Testing](../test/live-unit-testing-intro.md).

## <a name="generate-unit-tests-with-intellitest"></a>Generar pruebas unitarias con IntelliTest

Cuando ejecuta Intelltest, puede ver fácilmente qué pruebas son las que fallan y agregar cualquier código para corregirlas. Puede seleccionar las pruebas generadas que quiere guardar en un proyecto de prueba para proporcionar un conjunto de regresión. Cuando cambie el código, vuelva a ejecutar IntelliTest para mantener sincronizadas las pruebas generadas con los cambios de código. Para obtener información sobre cómo hacerlo, vea [Generar pruebas unitarias para el código con IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md).

![Generar pruebas unitarias con IntelliTest](media/intellitest.png)

## <a name="run-unit-tests-with-test-explorer"></a>Ejecutar pruebas unitarias con el Explorador de pruebas

Con el **Explorador de pruebas** puede ejecutar pruebas unitarias de Visual Studio o proyectos de prueba unitaria de terceros, agrupar pruebas en categorías, filtrar la lista de pruebas, y crear, guardar y ejecutar las listas de reproducción de pruebas. También puede depurar las pruebas, y analizar la cobertura de código y el rendimiento de la prueba. Para obtener información sobre cómo hacerlo, vea [Ejecutar pruebas unitarias con el Explorador de pruebas](../test/run-unit-tests-with-test-explorer.md).

![Ejecutar pruebas unitarias con el Explorador de pruebas](media/testexplorer.png)

## <a name="use-code-coverage-to-determine-how-much-code-is-being-tested"></a>Usar cobertura de código para determinar la cantidad de código que se está probando

Para determinar qué proporción de código del proyecto se está probando realmente mediante pruebas codificadas como pruebas unitarias, se puede utilizar la característica de cobertura de código de Visual Studio. Para restringir con eficacia los errores, las pruebas deberían ensayar una proporción considerable del código. Para obtener información sobre cómo hacerlo, vea [Usar cobertura de código para determinar la cantidad de código que se está probando](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

## <a name="use-a-different-unit-test-framework"></a>Usar otro marco de pruebas unitarias

Es posible ejecutar pruebas unitarias en Visual Studio con un marco de pruebas de un tercero, como Boost, Google y NUnit. Utilice el complemento de ese marco de trabajo a fin de que el ejecutor de pruebas de Visual Studio pueda funcionar con él.

Estos son los pasos que permiten habilitar los marcos de pruebas de terceros:

1. En la barra de menús, elija **Herramientas** > **Extensiones y actualizaciones**.

1. En el cuadro de diálogo **Extensiones y actualizaciones**, expanda la categoría **En línea** y, después, elija **Visual Studio Marketplace**. A continuación, elija **Herramientas** > **Pruebas**.

   ![Visual Studio Marketplace](media/extensions-and-updates-testing.png)

1. Seleccione el marco o el adaptador que quiera instalar y, después, elija **Descargar**.

1. Cree un proyecto de biblioteca de clases y agréguelo a su solución.

   ![Asignar un nombre al proyecto de biblioteca de clases y agregarlo](media/create3rdpartyunittest3.png)

1. Instale el complemento. En el **Explorador de soluciones**, seleccione el proyecto de biblioteca de clases y, después, haga clic con el botón derecho y elija **Administrar paquetes NuGet** en el menú contextual.

   ![Administrar paquetes NuGet para instalar el complemento](media/create3rdpartyunittest3a.png)

   [NuGet](https://www.nuget.org/) es una extensión de Visual Studio que puede usar para agregar y actualizar bibliotecas y herramientas para sus proyectos.

1. En la ventana **Administrador de paquetes NuGet**, busque y seleccione el complemento y, después, elija **Instalar**.

   ![Instalar el marco de terceros](media/create3rdpartyunittest4.png)

   En el proyecto se hace referencia al marco.

   ![La referencia del marco de pruebas unitarias de terceros se agrega a la solución](media/create3rdpartyunittest6.png)

1. En el nodo **Referencias** del proyecto de biblioteca de clases, seleccione **Agregar referencia**.

   ![Agregar una referencia al proyecto](media/createunittest6.png)

1. En el cuadro de diálogo **Administrador de referencias**, seleccione el proyecto que contiene el código que va a probar.

   ![Seleccionar el proyecto de código que va a probar](media/createunittest7.png)

1. Codifique la prueba unitaria.

   ![Adición de código al archivo de prueba unitaria](media/create3rdpartyunittest7.png)

## <a name="see-also"></a>Vea también

* [Tutorial: Crear y ejecutar pruebas unitarias en código administrado](walkthrough-creating-and-running-unit-tests-for-managed-code.md)
* [Crear un comando de pruebas unitarias](create-unit-tests-menu.md)
* [Generate tests with IntelliTest](generate-unit-tests-for-your-code-with-intellitest.md) (Generar pruebas con IntelliTest)
* [Ejecutar pruebas con el Explorador de pruebas](run-unit-tests-with-test-explorer.md)
* [Determine code coverage](using-code-coverage-to-determine-how-much-code-is-being-tested.md) (Determinar la cobertura de código)
* [Mejorar la calidad del código](improve-code-quality.md)