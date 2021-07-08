---
title: 'Tutorial: Creación de una aplicación de consola de C# sencilla'
description: Aprenda a crear una aplicación de consola de C# en Visual Studio mediante un procedimiento paso a paso.
ms.custom: vs-acquisition, get-started
ms.date: 02/10/2021
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: j-martens
ms.author: jmartens
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 5f155c2477c97b6f0d18a4cfd3d54386aee68dd9
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390377"
---
# <a name="tutorial-create-a-simple-c-console-app-in-visual-studio"></a>Tutorial: Creación de una aplicación de consola de C# sencilla en Visual Studio

En este tutorial para C#, usará Visual Studio para crear y ejecutar una aplicación de consola y explorar algunas características del entorno de desarrollo integrado (IDE) de Visual Studio mientras lo hace.

::: moniker range="vs-2017"

Si todavía no ha instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) para instalarlo de forma gratuita.

::: moniker-end

::: moniker range="vs-2019"

Si todavía no ha instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads) para instalarlo de forma gratuita.

::: moniker-end

::: moniker range="vs-2022"

Si todavía no ha instalado Visual Studio 2022 Preview, vaya a la página [Descargas de Visual Studio 2022 Preview](https://visualstudio.microsoft.com/vs/preview/vs2022) para instalarlo de forma gratuita.

::: moniker-end

## <a name="create-a-project"></a>Crear un proyecto

Para empezar, crearemos un proyecto de aplicación de C#. En el tipo de proyecto se incluyen todos los archivos de plantilla que vamos a necesitar, sin necesidad de agregar nada más.

::: moniker range="vs-2017"

1. Abra Visual Studio 2017.

2. En la barra de menús superior, elija **Archivo** > **Nuevo** > **Proyecto**.
   (Como alternativa, presione **Ctrl**+**Mayús**+**N**).

3. En el panel izquierdo del cuadro de diálogo **Nuevo proyecto**, expanda **C#** y elija **.NET Core**. En el panel central, elija **Aplicación de consola (.NET Core)** . Después, asigne al archivo el nombre **_Calculator_**.

   ![Plantilla de proyecto Aplicación de consola (.NET Core) en el cuadro de diálogo Nuevo proyecto en el IDE de Visual Studio](./media/new-project-csharp-calculator-console-app.png)

### <a name="add-a-workload-optional"></a>Agregar una carga de trabajo (opcional)

Si no ve la plantilla de proyecto **Aplicación de consola (.NET Core)** , puede obtenerla si agrega la carga de trabajo **Desarrollo multiplataforma de .NET Core**. Esta es la manera de hacerlo.

#### <a name="option-1-use-the-new-project-dialog-box"></a>Opción 1: Uso del cuadro de diálogo Nuevo proyecto

1. Elija el vínculo **Abrir el Instalador de Visual Studio** en el panel de la izquierda del cuadro de diálogo **Nuevo proyecto**.

   ![Elija el vínculo Abrir el Instalador de Visual Studio del cuadro de diálogo Nuevo proyecto](./media/csharp-open-visual-studio-installer-generic-dark.png)

1. Se iniciará el Instalador de Visual Studio. Elija la carga de trabajo **Desarrollo multiplataforma de .NET Core** y, después, elija **Modificar**.

   ![Carga de trabajo Desarrollo multiplataforma de .NET Core en el instalador de Visual Studio](./media/dot-net-core-xplat-dev-workload.png)

#### <a name="option-2-use-the-tools-menu-bar"></a>Opción 2: Uso de la barra del menú Herramientas

1. Cancele para salir del cuadro de diálogo **Nuevo proyecto** y, en la barra de menús superior, seleccione **Herramientas** > **Obtener herramientas y características**.

1. Se iniciará el Instalador de Visual Studio. Elija la carga de trabajo **Desarrollo multiplataforma de .NET Core** y, después, elija **Modificar**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Abra Visual Studio.

1. En la ventana de inicio, elija **Crear un proyecto nuevo**.

   ![Visualización de la ventana "Crear un proyecto"](../../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. En la ventana **Crear un nuevo proyecto**, elija **C#** en la lista Idioma. A continuación, seleccione **Windows** en la lista Plataforma y **Consola** en la lista Tipos de proyecto. 

   Después de aplicar los filtros de lenguaje, plataforma y tipo de proyecto, elija la plantilla **Aplicación de consola** y, luego, **Siguiente**.

    :::image type="content" source="./media/vs-2019/csharp-create-new-project-console-net-core.png" alt-text="Elija la plantilla C# para Aplicación de consola (.NET Framework).":::

   > [!NOTE]
   > Si no ve la plantilla **Aplicación de consola**, puede instalarla desde la ventana **Crear un nuevo proyecto**. En el mensaje **¿No encuentra lo que busca?** , elija el vínculo **Instalar más herramientas y características**.
   >
   > ![Vínculo "Instalar más herramientas y características" del mensaje "¿No encuentra lo que busca?" que aparece en la ventana "Crear proyecto"](../../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Luego, en el Instalador de Visual Studio, elija la carga de trabajo **Desarrollo multiplataforma de .NET Core**.
   >
   > ![Carga de trabajo Desarrollo multiplataforma de .NET Core en el instalador de Visual Studio](./media/dot-net-core-xplat-dev-workload.png)
   >
   > Después, elija el botón **Modificar** en el Instalador de Visual Studio. Es posible que se le pida que guarde su trabajo; si es así, hágalo. Seguidamente, elija **Continuar** para instalar la carga de trabajo. Luego, vuelva al paso 2 de este procedimiento "[Crear un proyecto](#create-a-project)".

1. En la ventana **Configurar el nuevo proyecto**, escriba *Calculator* en el cuadro **Nombre del proyecto**. Después, elija **Siguiente**.

    :::image type="content" source="./media/vs-2019/csharp-name-your-calculator-project.png" alt-text="En la ventana &quot;Configurar el nuevo proyecto&quot;, asigne al proyecto el nombre &quot;Calculator&quot;.":::
   
1. En la ventana **Información adicional**, **.NET Core 3.1** ya debe estar seleccionado para la plataforma de destino. Si no es así, seleccione **.NET Core 3.1**. Luego, elija **Crear**.

    :::image type="content" source="./media/vs-2019/csharp-target-framework.png" alt-text="En la ventana &quot;Información adicional&quot;, asegúrese de que está seleccionado .NET Core 3.1":::

   Visual Studio abre el nuevo proyecto, que incluye código predeterminado de "Hola mundo".

::: moniker-end

## <a name="create-the-app"></a>Creación de la aplicación

En primer lugar, exploraremos algunos cálculos de enteros básicos en C#. Después, agregaremos código para crear una calculadora básica. Después de eso, depuraremos la aplicación para buscar y corregir errores. Por último, perfeccionaremos el código para que sea más eficaz.

### <a name="explore-integer-math"></a>Análisis de las operaciones matemáticas con enteros

Empecemos con algunos cálculos básicos de enteros en C#.

1. En el editor de código, elimine el código predeterminado "Hello World".

    ![Eliminar el código "Hello World" predeterminado de la nueva aplicación de calculadora](./media/csharp-console-calculator-deletehelloworld.png)

   En concreto, elimine la línea que dice `Console.WriteLine("Hello World!");`.

1. En su lugar, escriba este código:

    ```csharp
            int a = 42;
            int b = 119;
            int c = a + b;
            Console.WriteLine(c);
            Console.ReadKey();
    ```

    Tenga en cuenta que, al hacerlo, la función IntelliSense en Visual Studio le ofrece la opción de autocompletar la entrada.

    > [!NOTE]
    > La animación siguiente no está pensada para duplicar el código anterior. Su único fin es mostrar cómo funciona la característica Autocompletar.

    ![Animación de código de cálculos de enteros que muestra la función autocompletar de IntelliSense en el IDE de Visual Studio](./media/integer-math-intellisense.gif)

1. Elija el botón verde **Inicio** junto a **Calculadora** para compilar y ejecutar el programa, o presione **F5**.

   ![Elección del botón Calculator para ejecutar la aplicación desde la barra de herramientas](./media/csharp-console-calculator-button.png)

   Se abre una ventana de consola que muestra la suma de 42+119, cuyo resultado es **161**.

    ![Ventana de consola que muestra los resultados de cálculos de enteros](./media/csharp-console-integer-math.png)

1. **(Opcional)** Puede modificar el operador para cambiar el resultado. Por ejemplo, puede cambiar el operador `+` en la línea de código `int c = a + b;` por `-` para la resta, `*` para la multiplicación o `/` para la división. A continuación, al ejecutar el programa, el resultado también cambia.

1. Cierre la ventana de la consola.

### <a name="add-code-to-create-a-calculator"></a>Incorporación de código para crear una calculadora

Ahora vamos a agregar al proyecto un conjunto más complejo de código de la calculadora.

1. Elimine todo el código que vea en el editor de código.

1. Escriba o pegue el siguiente código nuevo en el editor de código:

    ```csharp
    using System;

    namespace Calculator
    {
        class Program
        {
            static void Main(string[] args)
            {
                // Declare variables and then initialize to zero.
                int num1 = 0; int num2 = 0;

                // Display title as the C# console calculator app.
                Console.WriteLine("Console Calculator in C#\r");
                Console.WriteLine("------------------------\n");

                // Ask the user to type the first number.
                Console.WriteLine("Type a number, and then press Enter");
                num1 = Convert.ToInt32(Console.ReadLine());

                // Ask the user to type the second number.
                Console.WriteLine("Type another number, and then press Enter");
                num2 = Convert.ToInt32(Console.ReadLine());

                // Ask the user to choose an option.
                Console.WriteLine("Choose an option from the following list:");
                Console.WriteLine("\ta - Add");
                Console.WriteLine("\ts - Subtract");
                Console.WriteLine("\tm - Multiply");
                Console.WriteLine("\td - Divide");
                Console.Write("Your option? ");

                // Use a switch statement to do the math.
                switch (Console.ReadLine())
                {
                    case "a":
                        Console.WriteLine($"Your result: {num1} + {num2} = " + (num1 + num2));
                        break;
                    case "s":
                        Console.WriteLine($"Your result: {num1} - {num2} = " + (num1 - num2));
                        break;
                    case "m":
                        Console.WriteLine($"Your result: {num1} * {num2} = " + (num1 * num2));
                        break;
                    case "d":
                        Console.WriteLine($"Your result: {num1} / {num2} = " + (num1 / num2));
                        break;
                }
                // Wait for the user to respond before closing.
                Console.Write("Press any key to close the Calculator console app...");
                Console.ReadKey();
            }
        }
    }
    ```

1. Elija **Calculator** para ejecutar el programa, o bien presione **F5**.

   ![Elección del botón Calculator para ejecutar la aplicación desde la barra de herramientas](./media/csharp-console-calculator-button.png)

   Se abre una ventana de consola.

1. Vea la aplicación en la ventana de consola y, después, siga las indicaciones para agregar los números **42** y **119**.

   La ventana de consola debe ser similar a la de la siguiente captura de pantalla:

    ![Ventana de consola en la que se muestra la aplicación Calculator y que incluye mensajes sobre las acciones que se deben realizar](./media/csharp-console-calculator.png)

### <a name="add-functionality-to-the-calculator"></a>Incorporación de funcionalidad a la calculadora

Vamos a retocar el código para agregarle más funcionalidad.

### <a name="add-decimals"></a>Agregar decimales

En este momento, la aplicación Calculator acepta y devuelve números enteros, Pero será más precisa si agregamos código que permita incluir decimales.

Como se muestra en la siguiente captura de pantalla, si ejecutamos la aplicación y dividimos el número 42 entre el número 119, el resultado es 0 (cero), lo cual no es correcto.

![Ventana de consola que muestra una aplicación Calculator que no devuelve un número con decimales como resultado](./media/csharp-console-calculator-nodecimal.png)

Vamos a corregir el código de forma que dé cabida a los decimales.

1. Presione **Ctrl** + **B** para abrir el control **Buscar y reemplazar**.

1. Cambie cada instancia de la variable `int` por `float`.

   Asegúrese de que alterna **Coincidir mayúsculas y minúsculas** (**Alt**+**C**) y **Solo palabras completas** (**Alt**+**W**) en el control **Buscar y reemplazar**.

    ![Animación del control Buscar y reemplazar donde se muestra cómo cambiar la variable int a float](./media/find-replace-control-animation.gif)

1. Vuelva a ejecutar la aplicación Calculator y divida el número **42** entre el número **119**.

   Fíjese en que ahora la aplicación devuelve un número con decimales en lugar de cero.

    ![Ventana de consola que muestra una aplicación Calculator que ahora devuelve un número con decimales como resultado](./media/csharp-console-calculator-decimal.png)

Sin embargo, la aplicación genera solo un resultado decimal. Vamos a hacer algunos retoques más en el código para que la aplicación calcule decimales también.

1. Use el control **Buscar y reemplazar** (**Ctrl** + **B**) para cambiar cada instancia de la variable `float` a `double` y cambiar cada instancia del método `Convert.ToInt32` a `Convert.ToDouble`.

1. Ejecute la aplicación Calculator y divida el número **42.5** entre el número **119.75**.

   Fíjese en que ahora la aplicación acepta valores decimales y devuelve un número decimal más largo como resultado.

    ![Ventana de consola que muestra una aplicación Calculator que ahora acepta valores decimales y devuelve un número decimal más largo como resultado](./media/csharp-console-calculator-usedecimals.png)

    (Corregiremos el número de posiciones decimales en la sección [Revisar el código](#revise-the-code)).

## <a name="debug-the-app"></a>Depurar la aplicación

Hemos mejorado nuestra aplicación de calculadora básica, pero todavía carece de notificaciones de error que permitan controlar excepciones, como los errores que los usuarios cometen al escribir.

Por ejemplo, si se intenta dividir un número por cero o especificar un carácter alfanumérico cuando la aplicación espera uno numérico (o viceversa), la aplicación puede dejar de funcionar, devolver un error o devolver un resultado no numérico inesperado.

Vamos a ver algunos errores comunes de entrada de usuario, a localizarlos en el depurador si aparecen allí y a corregirlos en el código.

> [!TIP]
> Para más información sobre el depurador y cómo funciona, vea la página [Primer vistazo al depurador de Visual Studio](../../debugger/debugger-feature-tour.md).

### <a name="fix-the-divide-by-zero-error"></a>Corregir el error "división entre cero"

Al intentar dividir un número por cero, es posible que la aplicación de consola se inmovilice y, luego, muestre el problema en el editor de código.

   ![Captura de pantalla del editor de código de Visual Studio en la que se muestra una línea resaltada en amarillo y un error de excepción no controlada para "Attempted to divide by zero" (Intento de división entre cero).](./media/csharp-console-calculator-dividebyzero-error.png)

> [!NOTE]
> A veces, la aplicación no se inmoviliza ni el depurador muestra un error de división por cero, sino que la aplicación puede devolver un resultado no numérico inesperado, como un símbolo de infinito. La corrección de código siguiente sigue siendo válida.

Vamos a cambiar el código para controlar este error.

1. Elimine el código que aparece directamente entre `case "d":` y el comentario `// Wait for the user to respond before closing`.

1. Reemplácelo por el código siguiente:

   ```csharp
            // Ask the user to enter a non-zero divisor until they do so.
                while (num2 == 0)
                {
                    Console.WriteLine("Enter a non-zero divisor: ");
                    num2 = Convert.ToInt32(Console.ReadLine());
                }
                Console.WriteLine($"Your result: {num1} / {num2} = " + (num1 / num2));
                break;
        }
    ```

   Después de agregar el código, la sección con la instrucción `switch` debe ser similar a la de la siguiente captura de pantalla:

   ![Sección "switch" revisada en el editor de código de Visual Studio](./media/csharp-console-calculator-switch-code.png)

Ahora, cuando dividimos un número entre cero, la aplicación nos pedirá otro número. Mejor aún: no parará de pedirlo hasta que proporcionemos un número distinto de cero.

   ![Captura de pantalla del editor de código de Visual Studio en la que se muestra el código de la instrucción switch con la comprobación de la entrada de un divisor distinto de cero agregada.](./media/csharp-console-calculator-dividebyzero.png)

### <a name="fix-the-format-error"></a>Corregir el error de "formato"

Si introduce un carácter alfanumérico cuando la aplicación espera un carácter numérico (o viceversa), la aplicación de consola se congela. Luego, Visual Studio señala qué es incorrecto en el editor de código.

   ![Editor de código de Visual Studio que muestra un error de formato](./media/csharp-console-calculator-format-error.png)

Para corregir este error, debemos refactorizar el código que hemos escrito anteriormente.

#### <a name="revise-the-code"></a>Revisar el código

En lugar de usar la clase `program` para controlar todo el código, dividiremos nuestra aplicación en dos clases: `Calculator` y `Program`.

La clase `Calculator` controlará la mayor parte del trabajo de cálculo, mientras que la clase `Program` controlará la interfaz de usuario y el trabajo de captura de errores.

Comencemos.

1. Elimine todo en el espacio de nombres `Calculator` entre las llaves de apertura y cierre:

    ```csharp
    using System;

    namespace Calculator
    {
        
    }
    ```

1. Después, agregue una nueva clase `Calculator`, como se indica a continuación:

    ```csharp
    class Calculator
    {
        public static double DoOperation(double num1, double num2, string op)
        {
            double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.

            // Use a switch statement to do the math.
            switch (op)
            {
                case "a":
                    result = num1 + num2;
                    break;
                case "s":
                    result = num1 - num2;
                    break;
                case "m":
                    result = num1 * num2;
                    break;
                case "d":
                    // Ask the user to enter a non-zero divisor.
                    if (num2 != 0)
                    {
                        result = num1 / num2;
                    }
                    break;
                // Return text for an incorrect option entry.
                default:
                    break;
            }
            return result;
        }
    }

    ```

1. Luego, agregue una nueva clase `Program`, como se indica a continuación:

    ```csharp
    class Program
    {
        static void Main(string[] args)
        {
            bool endApp = false;
            // Display title as the C# console calculator app.
            Console.WriteLine("Console Calculator in C#\r");
            Console.WriteLine("------------------------\n");

            while (!endApp)
            {
                // Declare variables and set to empty.
                string numInput1 = "";
                string numInput2 = "";
                double result = 0;

                // Ask the user to type the first number.
                Console.Write("Type a number, and then press Enter: ");
                numInput1 = Console.ReadLine();

                double cleanNum1 = 0;
                while (!double.TryParse(numInput1, out cleanNum1))
                {
                    Console.Write("This is not valid input. Please enter an integer value: ");
                    numInput1 = Console.ReadLine();
                }

                // Ask the user to type the second number.
                Console.Write("Type another number, and then press Enter: ");
                numInput2 = Console.ReadLine();

                double cleanNum2 = 0;
                while (!double.TryParse(numInput2, out cleanNum2))
                {
                    Console.Write("This is not valid input. Please enter an integer value: ");
                    numInput2 = Console.ReadLine();
                }

                // Ask the user to choose an operator.
                Console.WriteLine("Choose an operator from the following list:");
                Console.WriteLine("\ta - Add");
                Console.WriteLine("\ts - Subtract");
                Console.WriteLine("\tm - Multiply");
                Console.WriteLine("\td - Divide");
                Console.Write("Your option? ");

                string op = Console.ReadLine();

                try
                {
                    result = Calculator.DoOperation(cleanNum1, cleanNum2, op);
                    if (double.IsNaN(result))
                    {
                        Console.WriteLine("This operation will result in a mathematical error.\n");
                    }
                    else Console.WriteLine("Your result: {0:0.##}\n", result);
                }
                catch (Exception e)
                {
                    Console.WriteLine("Oh no! An exception occurred trying to do the math.\n - Details: " + e.Message);
                }

                Console.WriteLine("------------------------\n");

                // Wait for the user to respond before closing.
                Console.Write("Press 'n' and Enter to close the app, or press any other key and Enter to continue: ");
                if (Console.ReadLine() == "n") endApp = true;

                Console.WriteLine("\n"); // Friendly linespacing.
            }
            return;
        }
    }
    ```

1. Elija **Calculator** para ejecutar el programa, o bien presione **F5**.

1. Siga las indicaciones y divida el número **42** entre el número **119**. La ventana de consola debe ser similar a la de la siguiente captura de pantalla:

    ![Ventana de consola en la que se muestra la aplicación Calculator refactorizada, que incluye mensajes sobre las acciones que se deben realizar y control de errores de entrada incorrecta](./media/csharp-console-calculator-refactored.png)

    Fíjese en que tiene la opción de especificar más ecuaciones hasta que decida cerrar la aplicación de consola. También hemos reducido el número de posiciones decimales en el resultado.

## <a name="close-the-app"></a>Cierre la aplicación

1. Si aún no lo ha hecho, cierre la aplicación de calculadora.

1. Cierre el panel **Salida** en Visual Studio.

   ![Cierre del panel Salida en Visual Studio](./media/csharp-calculator-close-output-pane.png)

1. En Visual Studio, presione **Ctrl**+**G** para guardar la aplicación.

1. Cierre Visual Studio.

## <a name="code-complete"></a>Código completo

Durante este tutorial, hemos realizado muchos cambios en la aplicación de calculadora. Ahora la aplicación controla los recursos de cálculo más eficazmente y trata la mayoría de los errores de entrada de usuario.

Este es el código completo:

```csharp

using System;

namespace Calculator
{
    class Calculator
    {
        public static double DoOperation(double num1, double num2, string op)
        {
            double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.

            // Use a switch statement to do the math.
            switch (op)
            {
                case "a":
                    result = num1 + num2;
                    break;
                case "s":
                    result = num1 - num2;
                    break;
                case "m":
                    result = num1 * num2;
                    break;
                case "d":
                    // Ask the user to enter a non-zero divisor.
                    if (num2 != 0)
                    {
                        result = num1 / num2;
                    }
                    break;
                // Return text for an incorrect option entry.
                default:
                    break;
            }
            return result;
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            bool endApp = false;
            // Display title as the C# console calculator app.
            Console.WriteLine("Console Calculator in C#\r");
            Console.WriteLine("------------------------\n");

            while (!endApp)
            {
                // Declare variables and set to empty.
                string numInput1 = "";
                string numInput2 = "";
                double result = 0;

                // Ask the user to type the first number.
                Console.Write("Type a number, and then press Enter: ");
                numInput1 = Console.ReadLine();

                double cleanNum1 = 0;
                while (!double.TryParse(numInput1, out cleanNum1))
                {
                    Console.Write("This is not valid input. Please enter an integer value: ");
                    numInput1 = Console.ReadLine();
                }

                // Ask the user to type the second number.
                Console.Write("Type another number, and then press Enter: ");
                numInput2 = Console.ReadLine();

                double cleanNum2 = 0;
                while (!double.TryParse(numInput2, out cleanNum2))
                {
                    Console.Write("This is not valid input. Please enter an integer value: ");
                    numInput2 = Console.ReadLine();
                }

                // Ask the user to choose an operator.
                Console.WriteLine("Choose an operator from the following list:");
                Console.WriteLine("\ta - Add");
                Console.WriteLine("\ts - Subtract");
                Console.WriteLine("\tm - Multiply");
                Console.WriteLine("\td - Divide");
                Console.Write("Your option? ");

                string op = Console.ReadLine();

                try
                {
                    result = Calculator.DoOperation(cleanNum1, cleanNum2, op);
                    if (double.IsNaN(result))
                    {
                        Console.WriteLine("This operation will result in a mathematical error.\n");
                    }
                    else Console.WriteLine("Your result: {0:0.##}\n", result);
                }
                catch (Exception e)
                {
                    Console.WriteLine("Oh no! An exception occurred trying to do the math.\n - Details: " + e.Message);
                }

                Console.WriteLine("------------------------\n");

                // Wait for the user to respond before closing.
                Console.Write("Press 'n' and Enter to close the app, or press any other key and Enter to continue: ");
                if (Console.ReadLine() == "n") endApp = true;

                Console.WriteLine("\n"); // Friendly linespacing.
            }
            return;
        }
    }
}

```

## <a name="next-steps"></a>Pasos siguientes

:::moniker range="vs-2017"

Continúe con más tutoriales:

> [!div class="nextstepaction"]
> [Tutoriales de C#](/dotnet/csharp/tutorials)

> [!div class="nextstepaction"]
> [Un paseo por el IDE de Visual Studio](../visual-studio-ide.md)

:::moniker-end

:::moniker range=">=vs-2019"

Continúe con la segunda parte de este tutorial:

> [!div class="nextstepaction"]
> [Continuar con la parte 2](tutorial-console-part-2.md)
:::moniker-end

## <a name="see-also"></a>Vea también

* [IntelliSense para C#](../../ide/visual-csharp-intellisense.md)
* [Información sobre cómo depurar código de C# con Visual Studio](tutorial-debugger.md)
