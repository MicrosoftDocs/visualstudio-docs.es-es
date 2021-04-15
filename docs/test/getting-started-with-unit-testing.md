---
title: Introducción a las pruebas unitarias
description: Use Visual Studio para definir y ejecutar pruebas unitarias para conservar el estado del código y detectar errores y fallos antes de que lo hagan los clientes.
ms.custom: SEO-VS-2020
ms.date: 04/07/2020
ms.topic: tutorial
helpviewer_keywords:
- unit testing, create unit test plans
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1e1576f8865fc5945514ce6965cdba66a1cfda55
ms.sourcegitcommit: 3985d0ae8d6332f4682c82a10897763173d52961
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2021
ms.locfileid: "107386055"
---
# <a name="get-started-with-unit-testing"></a>Introducción a las pruebas unitarias

Use Visual Studio para definir y ejecutar pruebas unitarias para conservar el estado del código, garantizar la cobertura del código y detectar errores y fallos antes de que lo hagan los clientes. Ejecute las pruebas unitarias con frecuencia para asegurarse de que el código funciona correctamente.

En este artículo, el código y las ilustraciones usan C#, pero los conceptos y las características se aplican a los lenguajes .NET, C++, Python, JavaScript y TypeScript.

## <a name="create-unit-tests"></a>Crear pruebas unitarias

En esta sección se describe cómo crear un proyecto de prueba unitaria.

1. Abra el proyecto que quiere probar en Visual Studio.

   Para los fines de demostración de una prueba unitaria de ejemplo, en este artículo se prueba un proyecto de C# sencillo "Hola mundo" denominado **HelloWorldCore**. El código de ejemplo para dicho proyecto es el siguiente:

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

1. En el cuadro de diálogo Nuevo proyecto, busque una plantilla de proyecto de prueba unitaria para el marco de pruebas que quiera usar, como MSTest, y selecciónela.

   A partir de la versión 14.8 de Visual Studio 2017, los lenguajes de .NET incluyen plantillas integradas para NUnit y xUnit. Para C++, deberá seleccionar un marco de pruebas compatible con el lenguaje. Para Python, consulte el artículo [Configuración de pruebas unitarias para código de Python](../python/unit-testing-python-in-visual-studio.md) para configurar el proyecto de prueba.

   > [!TIP]
   > Para C#, puede crear proyectos de prueba unitaria a partir del código con un método más rápido. Para obtener más información, vea [Crear proyectos de prueba unitaria y métodos de prueba](../test/unit-test-basics.md#create-unit-test-projects-and-test-methods). Para usar este método con .NET Core o .NET Standard, se requiere Visual Studio 2019.

   En la ilustración siguiente se muestra una prueba unitaria de MSTest que es compatible con .NET.

   ::: moniker range=">=vs-2019"

   ![Plantilla de proyecto de prueba unitaria en Visual Studio 2019](media/vs-2019/add-new-test-project.png)

   Haga clic en **Siguiente**, elija un nombre para el proyecto de prueba y luego haga clic en **Crear**.

   ::: moniker-end

   ::: moniker range="vs-2017"

   ![Plantilla de proyecto de prueba unitaria en Visual Studio 2019](media/mstest-test-project-template.png)

   Elija un nombre para el proyecto de prueba, por ejemplo, HelloWorldTests, y haga clic en **Aceptar**.

   ::: moniker-end

   El proyecto se agrega a la solución.

   ![Proyecto de prueba unitaria en el Explorador de soluciones](media/vs-2019/solution-explorer.png)

1. En el proyecto de prueba unitaria, agregue una referencia al proyecto que quiere probar haciendo clic con el botón derecho en **Referencias** o **Dependencias** y luego elija **Agregar referencia**.

1. Seleccione el proyecto que contiene el código que va a probar y haga clic en **Aceptar**.

   ![Incorporación de una referencia de proyecto en Visual Studio](media/vs-2019/reference-manager.png)

1. Agregue código al método de prueba unitaria.

   Por ejemplo, puede usar el siguiente código de la pestaña de documentación adecuada para su marco de pruebas: MSTest, NUnit o xUnit (solo se admiten en .NET).

   ### <a name="mstest"></a>[MSTest](#tab/mstest)

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

   ### <a name="nunit"></a>[NUnit](#tab/nunit)

   ```csharp
   using NUnit.Framework;
   using System.IO;
   using System;

   namespace HelloWorldTests
   {
      public class Tests
      {
         private const string Expected = "Hello World!";

         [SetUp]
         public void Setup()
         {
         }
         [Test]
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

    ### <a name="xunit"></a>[xUnit](#tab/xunit)

    ```csharp
    using System;
    using Xunit;
    using System.IO;
    
    namespace HelloWorldTests
    {
        public class UnitTest1
        {
            private const string Expected = "Hello World!";
            [Fact]
            public void Test1()
            {
                using (var sw = new StringWriter())
                {
                    Console.SetOut(sw);
                    HelloWorldCore.Program.Main();
    
                    var result = sw.ToString().Trim();
                    Assert.Equal(Expected, result);
                }
            }
        }
    }
    ```

    ---

## <a name="run-unit-tests"></a>Ejecutar pruebas unitarias

1. Abra el [Explorador de pruebas](../test/run-unit-tests-with-test-explorer.md).

   ::: moniker range=">=vs-2019"
   Para abrir el Explorador de pruebas, elija **Probar** > **Explorador de pruebas** en la barra de menús superior (o presione **CTRL** + **E**, **T**).
   ::: moniker-end
   ::: moniker range="vs-2017"
   Para abrir el Explorador de pruebas, elija **Probar** > **Windows** > **Explorador de pruebas** en la barra de menús superior.
   ::: moniker-end

1. Haga clic en **Ejecutar todas** (o presione **CTRL** + **R**, **V**) para ejecutar las pruebas unitarias.

   ![Ejecutar pruebas unitarias en el Explorador de pruebas](media/vs-2019/test-explorer-run-all.png)

   Cuando se hayan completado las pruebas, una marca de verificación verde indica que una prueba se superó. Un icono "x" rojo indica que una prueba no se superó.

   ![Revisar los resultados de pruebas unitarias en el Explorador de pruebas](media/vs-2019/unit-test-passed.png)

> [!TIP]
> Puede usar el [Explorador de pruebas](../test/run-unit-tests-with-test-explorer.md) para ejecutar pruebas unitarias en el marco de pruebas integrado (MSTest) o en marcos de pruebas de terceros. Puede agrupar las pruebas en categorías, filtrar la lista de pruebas y crear, guardar y ejecutar listas de reproducción de pruebas. También puede depurar las pruebas, y analizar la cobertura de código y el rendimiento de la prueba.

## <a name="view-live-unit-test-results-visual-studio-enterprise"></a>Visualización de los resultados de pruebas unitarias en vivo (Visual Studio Enterprise)

Si está usando el marco de pruebas de MSTest, xUnit o NUnit en Visual Studio 2017 o versiones posteriores, puede ver los resultados en vivo de sus pruebas unitarias.

> [!NOTE]
> Para seguir estos pasos, se necesita Visual Studio Enterprise.

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

## <a name="use-a-third-party-test-framework"></a>Uso de un marco de pruebas de terceros

Es posible ejecutar pruebas unitarias en Visual Studio con un marco de pruebas de un tercero, como Boost, Google y NUnit, en función del lenguaje de programación. Para usar un marco de pruebas de terceros:

- Use el **Administrador de paquetes NuGet** para instalar el paquete NuGet correspondiente al marco de trabajo que prefiera.

- (.NET) A partir de la versión 14.6 de Visual Studio 2017, Visual Studio incluye plantillas de proyecto de prueba preconfiguradas para los marcos de pruebas de NUnit y xUnit. Estas plantillas también incluyen los paquetes de NuGet necesarios para habilitar la compatibilidad.

- (C++) En Visual Studio 2017 y versiones posteriores, algunos marcos, como Boost, ya están incluidos. Para obtener más información, vea [Escribir pruebas unitarias para C/C++ en Visual Studio](../test/writing-unit-tests-for-c-cpp.md).

Para agregar un proyecto de prueba unitaria:

1. Abra la solución que contiene el código que quiere probar.

2. Haga clic con el botón derecho en la solución en el **Explorador de soluciones** y seleccione **Agregar** > **Nuevo proyecto**.

3. Seleccione una plantilla de proyecto de prueba unitaria.

   En este ejemplo, seleccione [NUnit](https://nunit.org/).

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

6. Ejecute la prueba desde el **Explorador de pruebas** o haga clic con el botón derecho en el código de prueba y elija **Ejecutar pruebas** (o presione **CTRL** + **R**, **T**).

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Conceptos básicos de prueba unitaria](../test/unit-test-basics.md)

> [!div class="nextstepaction"]
> [Crear y ejecutar pruebas unitarias en código administrado](walkthrough-creating-and-running-unit-tests-for-managed-code.md)
