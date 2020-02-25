---
title: Introducción a las pruebas unitarias
ms.date: 02/13/2020
ms.topic: conceptual
helpviewer_keywords:
- unit testing, create unit test plans
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7ffbc5c6730fb4ca4d2f39732ad2a595de15bbf2
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2020
ms.locfileid: "77279324"
---
# <a name="get-started-with-unit-testing"></a>Introducción a las pruebas unitarias

Use Visual Studio para definir y ejecutar pruebas unitarias para conservar el estado del código, garantizar la cobertura del código y detectar errores y fallos antes de que lo hagan los clientes. Ejecute las pruebas unitarias con frecuencia para asegurarse de que el código funciona correctamente.

## <a name="create-unit-tests"></a>Crear pruebas unitarias

En esta sección se describe de forma general cómo se crea un proyecto de prueba unitaria.

1. Abra el proyecto que quiere probar en Visual Studio.

   Para los fines de demostración de una prueba unitaria de ejemplo, en este artículo se prueba un proyecto sencillo "Hola mundo" denominado **HelloWorldCore**. El código de ejemplo para dicho proyecto es el siguiente:

   ```csharp
   namespace HelloWorldCore

      public class Program
      {
         public static void Main()
         {
            Console.WriteLine("Hello World!");
         }
      }
   ```

1. En el **Explorador de soluciones**, seleccione el nodo de la solución. Después, en la barra de menús superior, seleccione **Archivo** > **Agregar** > **Nuevo proyecto**.

1. En el cuadro de diálogo Nuevo proyecto, busque una plantilla de proyecto de prueba unitaria para el marco de pruebas que quiera utilizar y selecciónela.

   ::: moniker range=">=vs-2019"

   ![Plantilla de proyecto de prueba unitaria en Visual Studio 2019](media/vs-2019/add-new-test-project.png)

   Haga clic en **Siguiente**, elija un nombre para el proyecto de prueba y luego haga clic en **Crear**.

   ::: moniker-end

   ::: moniker range="vs-2017"

   ![Plantilla de proyecto de prueba unitaria en Visual Studio 2019](media/mstest-test-project-template.png)

   Elija un nombre para el proyecto de prueba y haga clic en **Aceptar**.

   ::: moniker-end

   El proyecto se agrega a la solución.

   ![Proyecto de prueba unitaria en el Explorador de soluciones](media/vs-2019/solution-explorer.png)

1. En el proyecto de prueba unitaria, agregue una referencia al proyecto que quiere probar haciendo clic con el botón derecho en **Referencias** o **Dependencias** y luego elija **Agregar referencia**.

1. Seleccione el proyecto que contiene el código que va a probar y haga clic en **Aceptar**.

   ![Incorporación de una referencia de proyecto en Visual Studio](media/vs-2019/reference-manager.png)

1. Agregue código al método de prueba unitaria.

   Por ejemplo, para un proyecto de prueba MSTest o NUnit, podría usar el código siguiente:

   ```csharp
   using Microsoft.VisualStudio.TestTools.UnitTesting;
   using System.IO;
   using System;

   namespace HelloWorldTests
   {
      [TestClass]
      public class UnitTest1
      {
         private const string Expected = "Hello World!";
         [TestMethod]
         public void TestMethod1()
         {
            using (var sw = new StringWriter())
            {
               Console.SetOut(sw);
               HelloWorldCore.Program.Main();

               var result = sw.ToString().Trim();
               Assert.AreEqual(Expected, result);
            }
         }
      }
   }
   ```

> [!TIP]
> Para obtener un tutorial más detallado sobre la creación de pruebas unitarias, vea [Crear y ejecutar pruebas unitarias en código administrado](walkthrough-creating-and-running-unit-tests-for-managed-code.md).

## <a name="run-unit-tests"></a>Ejecutar pruebas unitarias

1. Abra el [Explorador de pruebas](../test/run-unit-tests-with-test-explorer.md).

   ::: moniker range=">=vs-2019"
   Para abrir el Explorador de pruebas, elija **Probar** > **Explorador de pruebas** en la barra de menús superior.
   ::: moniker-end
   ::: moniker range="vs-2017"
   Para abrir el Explorador de pruebas, elija **Probar** > **Windows** > **Explorador de pruebas** en la barra de menús superior.
   ::: moniker-end

1. Ejecute las pruebas unitarias haciendo clic en **Ejecutar todo**.

   ![Ejecutar pruebas unitarias en el Explorador de pruebas](media/vs-2019/test-explorer-run-all.png)

   Cuando se hayan completado las pruebas, una marca de verificación verde indica que una prueba se superó. Un icono "x" rojo indica que una prueba no se superó.

   ![Revisar los resultados de pruebas unitarias en el Explorador de pruebas](media/vs-2019/unit-test-passed.png)

> [!TIP]
> Puede usar el [Explorador de pruebas](../test/run-unit-tests-with-test-explorer.md) para ejecutar pruebas unitarias en el marco de pruebas integrado (MSTest) o en marcos de pruebas de terceros. Puede agrupar las pruebas en categorías, filtrar la lista de pruebas y crear, guardar y ejecutar listas de reproducción de pruebas. También puede depurar las pruebas, y analizar la cobertura de código y el rendimiento de la prueba.

## <a name="view-live-unit-test-results"></a>Ver los resultados de las pruebas unitarias en vivo

Si está usando el marco de pruebas de MSTest, xUnit o NUnit en Visual Studio 2017 o versiones posteriores, puede ver los resultados en vivo de sus pruebas unitarias.

> [!NOTE]
> Live Unit Testing solo está disponible en Enterprise Edition.

1. Active Live Unit Testing desde el menú **Probar** seleccionando **Probar** > **Live Unit Testing** > **Iniciar**.

   ::: moniker range="vs-2017"

   ![Activar las pruebas unitarias en vivo](media/live-test-results-start.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Live Unit Testing en Visual Studio 2019](media/vs-2019/start-live-unit-testing.png)

   ::: moniker-end

1. Vea los resultados de las pruebas dentro de la ventana del editor de código a medida que escribe y edita el código.

   ![Ver los resultados de las pruebas](media/vs-2019/live-unit-testing-results.png)

1. Haga clic en un indicador de resultado de la prueba para obtener más información, como, por ejemplo, los nombres de las pruebas que contemplan ese método.

   ![Seleccionar los indicadores de resultados de la prueba](media/vs-2019/live-unit-testing-details.png)

Para obtener más información sobre esta característica, vea [Live Unit Testing](../test/live-unit-testing-intro.md).

## <a name="generate-unit-tests-with-intellitest"></a>Generar pruebas unitarias con IntelliTest

Cuando ejecuta IntelliTest, puede ver qué pruebas son las que fallan y agregar cualquier código para corregirlas. Puede seleccionar las pruebas generadas que quiere guardar en un proyecto de prueba para proporcionar un conjunto de regresión. Cuando cambie el código, vuelva a ejecutar IntelliTest para mantener sincronizadas las pruebas generadas con los cambios de código. Para obtener información sobre cómo hacerlo, vea [Generar pruebas unitarias para el código con IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md).

> [!TIP]
> IntelliTest solo está disponible para código administrado que tenga como destino .NET Framework.

![Generar pruebas unitarias con IntelliTest](media/intellitest.png)

## <a name="analyze-code-coverage"></a>Análisis de la cobertura de código

Para determinar qué proporción de código del proyecto se está probando realmente mediante pruebas codificadas como pruebas unitarias, se puede utilizar la característica de cobertura de código de Visual Studio. Para restringir con eficacia los errores, las pruebas deberían ensayar una proporción considerable del código. Para obtener información sobre cómo hacerlo, vea [Usar cobertura de código para determinar la cantidad de código que se está probando](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

## <a name="use-a-third-party-test-framework"></a>Uso de un marco de pruebas de terceros

Es posible ejecutar pruebas unitarias en Visual Studio con un marco de pruebas de un tercero, como Boost, Google y NUnit. Use el **Administrador de paquetes NuGet** para instalar el paquete NuGet correspondiente al marco de trabajo que prefiera. O bien, en el caso de marcos de pruebas de xUnit y NUnit, Visual Studio incluye plantillas de proyecto de prueba preconfiguradas que incluyen los paquetes NuGet necesarios.

Para crear pruebas unitarias que usen [NUnit](https://nunit.org/):

1. Abra la solución que contiene el código que quiere probar.

2. Haga clic con el botón derecho en la solución en el **Explorador de soluciones** y seleccione **Agregar** > **Nuevo proyecto**.

3. Seleccione la platilla de proyecto **Proyecto de prueba de NUnit**.

   ::: moniker range=">=vs-2019"

   ![Plantilla de proyecto de prueba de NUnit en Visual Studio 2019](media/vs-2019/nunit-test-project-template.png)

   Haga clic en **Siguiente**, asigne un nombre al proyecto y haga clic en **Crear**.

   ::: moniker-end

   ::: moniker range="vs-2017"

   Asigne al proyecto un nombre y haga clic en **Aceptar** para crearlo.

   ::: moniker-end

   La plantilla de proyecto incluye referencias de NuGet para NUnit y NUnit3TestAdapter.

   ![Dependencias de NuGet de NUnit en el Explorador de soluciones](media/vs-2019/nunit-nuget-dependencies.png)

4. Agregue una referencia del proyecto de prueba al proyecto que contiene el código que quiera probar.

   Haga clic con el botón derecho en el proyecto en el **Explorador de soluciones** y, luego, seleccione **Agregar** > **Referencia**. (También puede agregar una referencia del menú contextual del nodo **Referencias** o **Dependencias**).

5. Agregue código a al método de prueba.

   ![Adición de código al archivo de prueba unitaria](media/vs-2019/unit-test-method.png)

6. Ejecute la prueba desde el **Explorador de pruebas** o haciendo clic con el botón derecho en el código de prueba y eligiendo **Run Test(s)** (Ejecutar pruebas).

## <a name="see-also"></a>Vea también

* [Tutorial: Crear y ejecutar pruebas unitarias en código administrado](walkthrough-creating-and-running-unit-tests-for-managed-code.md)
* [Crear un comando de pruebas unitarias](create-unit-tests-menu.md)
* [Generate tests with IntelliTest](generate-unit-tests-for-your-code-with-intellitest.md) (Generar pruebas con IntelliTest)
* [Ejecutar pruebas con el Explorador de pruebas](run-unit-tests-with-test-explorer.md)
* [Análisis de la cobertura de código](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
