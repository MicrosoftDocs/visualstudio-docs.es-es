---
title: Tutorial de desarrollo controlado por pruebas
ms.date: 07/24/2019
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: a264975014fea88126bbca0589fe037e629dae10
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "75566285"
---
# <a name="walkthrough-test-driven-development-using-test-explorer"></a>Tutorial: Desarrollo controlado por pruebas con el Explorador de pruebas

Cree pruebas unitarias que ayuden a mantener el código funcionando correctamente mediante cambios incrementales en él. Hay varios marcos que se pueden utilizar para escribir pruebas unitarias, incluidos algunos desarrollados por terceros. Algunos marcos de prueba son especiales para pruebas en plataformas o lenguajes diferentes. El Explorador de pruebas proporciona una sola interfaz para las pruebas unitarias en cualquiera de estos marcos. Para más información sobre cómo usar el **Explorador de pruebas**, consulte [Ejecutar pruebas unitarias con el Explorador de pruebas](run-unit-tests-with-test-explorer.md) y [Preguntas más frecuentes sobre el Explorador de pruebas](test-explorer-faq.md).

En este tutorial se muestra cómo desarrollar un método probado en C# con el marco de pruebas de Microsoft (MSTest). Se puede adaptar fácilmente a otros lenguajes o usar otros marcos de pruebas, como NUnit. Para más información, vea [Instalar marcos de prueba unitaria de terceros](install-third-party-unit-test-frameworks.md).

## <a name="create-a-test-and-generate-code"></a>Creación de una prueba y generación del código

1. Cree un proyecto de **biblioteca de clases .NET Standard**  en C#. Este proyecto contendrá el código que quiere probar. Asigne al proyecto el nombre **MyMath**.

2. En la misma solución, agregue un nuevo **proyecto de prueba de MSTest (.NET Core)** . Asigne al proyecto de prueba el nombre **MathTests**.

   ![Nuevo código y proyectos de prueba](../test/media/test-driven-development-ide.png)

3. Escriba un método de prueba simple que compruebe el resultado obtenido para una entrada específica. Agregue el código siguiente a la clase `UnitTest1`:

   ```csharp
   [TestMethod]
   public void BasicRooterTest()
   {
     // Create an instance to test:
     Rooter rooter = new Rooter();
     // Define a test input and output value:
     double expectedResult = 2.0;
     double input = expectedResult * expectedResult;
     // Run the method under test:
     double actualResult = rooter.SquareRoot(input);
     // Verify the result:
     Assert.AreEqual(expectedResult, actualResult, delta: expectedResult / 100);
   }
   ```

4. Genere un tipo a partir del código de prueba.

   1. Coloque el cursor en `Rooter` y, luego, en el menú de bombilla, elija **Generate tipo "Rooter"** ' > **Generar nuevo tipo**.

      ![Generación de una nueva acción rápida de tipo](media/test-driven-development-generate-new-type.png)

   2. En el cuadro de diálogo **Generar tipo**, establezca **Proyecto** en **MyMath**, el proyecto de biblioteca de clases y, luego, elija **Aceptar**.

      ![Cuadro de diálogo Generar tipo en Visual Studio 2019](media/test-driven-development-generate-type-dialog.png)

5. Genere un método a partir del código de prueba. Coloque el cursor en `SquareRoot` y, luego, en el menú de bombilla, elija **Generar método "Rooter.SquareRoot"** .

6. Ejecute la prueba unitaria.

   1. Para abrir el **Explorador de pruebas**, en el menú **Prueba**, elija **Windows** > **Explorador de pruebas**.

   2. En el **Explorador de pruebas**, elija el botón **Ejecutar todo** para ejecutar la prueba.

   La solución se compila y la prueba se ejecuta pero no se supera.

7. Seleccione el nombre de la prueba.

   Los detalles de la prueba aparecen en el panel **Resumen de los detalles de la prueba**.

   ![Resumen de los detalles de la prueba en el Explorador de pruebas](media/test-driven-development-test-detail-summary.png)

8. Seleccione el vínculo superior en **Seguimiento de la pila** para saltar a la ubicación en la que se produjo un error en la prueba.

En este punto, se ha creado una prueba y código auxiliar que se puede modificar para que la prueba se supere.

## <a name="verify-a-code-change"></a>Comprobación de un cambio en el código

1. En el archivo *Class1.cs*, mejore el código de `SquareRoot`:

    ```csharp
    public double SquareRoot(double input)
    {
        return input / 2;
    }
    ```

2. En el **Explorador de pruebas**, elija **Ejecutar todo**.

   La solución se compila y la prueba se ejecuta y se supera.

   ![Explorador de pruebas que muestra una prueba superada](../test/media/test-driven-development-passed-test.png)

## <a name="extend-the-range-of-inputs"></a>Extensión del intervalo de entradas

Para mejorar la confianza en que el código funcione en todos los casos, agregue pruebas que comprueben un intervalo más amplio de valores de entrada.

> [!TIP]
> Evite modificar las pruebas existentes que se completan correctamente. En su lugar, agregue nuevas pruebas. Cambie las pruebas existentes solo si cambian los requisitos de usuario. Esta directiva ayuda a garantizar que no se pierda la función existente mientras se trabaja para ampliar el código.

1. En la clase de prueba, agregue la siguiente prueba para un intervalo de valores de entrada:

    ```csharp
    [TestMethod]
    public void RooterValueRange()
    {
        // Create an instance to test.
        Rooter rooter = new Rooter();

        // Try a range of values.
        for (double expected = 1e-8; expected < 1e+8; expected *= 3.2)
        {
            RooterOneValue(rooter, expected);
        }
    }

    private void RooterOneValue(Rooter rooter, double expectedResult)
    {
        double input = expectedResult * expectedResult;
        double actualResult = rooter.SquareRoot(input);
        Assert.AreEqual(expectedResult, actualResult, delta: expectedResult / 1000);
    }
    ```

2. En el **Explorador de pruebas**, elija **Ejecutar todo**.

   La nueva prueba no se supera, aunque la primera aún se completa correctamente. Para encontrar el punto de error, seleccione la prueba con errores y, luego, examine los detalles del panel **Resumen de los detalles de la prueba**.

3. Inspeccione el método que se está probando para ver qué puede ser incorrecto. Modifique el código `SquareRoot` de la forma siguiente:

    ```csharp
    public double SquareRoot(double input)
    {
      double result = input;
      double previousResult = -input;
      while (Math.Abs(previousResult - result) > result / 1000)
      {
        previousResult = result;
        result = result - (result * result - input) / (2 * result);
      }
      return result;
    }
    ```

4. En el **Explorador de pruebas**, elija **Ejecutar todo**.

   Ahora ambas pruebas se completan correctamente.

## <a name="add-tests-for-exceptional-cases"></a>Agregue pruebas para casos excepcionales

1. Agregue una nueva prueba para entradas negativas:

    ```csharp
    [TestMethod]
    public void RooterTestNegativeInputx()
    {
        Rooter rooter = new Rooter();
        try
        {
            rooter.SquareRoot(-10);
        }
        catch (System.ArgumentOutOfRangeException)
        {
            return;
        }
        Assert.Fail();
    }
    ```

2. En el **Explorador de pruebas**, elija **Ejecutar todo**.

   El método bajo prueba entra en bucle y debe cancelarse manualmente.

3. Elija **Cancelar** en la barra de herramientas de **Explorador de pruebas**.

   La prueba deja de ejecutarse.

4. Corrija el código `SquareRoot`; para ello, agregue la siguiente instrucción `if` al principio del método:

    ```csharp
    public double SquareRoot(double input)
    {
        if (input <= 0.0)
        {
            throw new ArgumentOutOfRangeException();
        }
        ...
    ```

5. En el **Explorador de pruebas**, elija **Ejecutar todo**.

   Todas las pruebas se completan correctamente.

## <a name="refactor-the-code-under-test"></a>Refactorizar el código en pruebas

Refactorice el código, pero no cambie las pruebas.

> [!TIP]
> Una *refactorización* es un cambio que está pensado para que el código se ejecute mejor o para que sea más fácil de comprender. No está pensado para alterar el comportamiento del código y, por tanto, no se cambian las pruebas.
>
> Se recomienda realizar los pasos de refactorización independientemente de los pasos que amplían la funcionalidad. Mantener las pruebas sin cambios aporta la confianza de no haber introducido errores accidentalmente durante la refactorización.

1. Cambie la línea que calcula `result` en el método `SquareRoot` de la manera siguiente:

    ```csharp
    public double SquareRoot(double input)
    {
        if (input <= 0.0)
        {
            throw new ArgumentOutOfRangeException();
        }

        double result = input;
        double previousResult = -input;
        while (Math.Abs(previousResult - result) > result / 1000)
        {
            previousResult = result;
            result = (result + input / result) / 2;
            //was: result = result - (result * result - input) / (2*result);
        }
        return result;
    }
    ```

2. Elija **Ejecutar todo** y compruebe que todas las pruebas se siguen superando.

   ![Explorador de pruebas que muestra 3 pruebas superadas](../test/media/test-driven-development-three-passed-tests.png)
