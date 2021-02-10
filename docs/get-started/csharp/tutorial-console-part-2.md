---
title: 'Tutorial: Extensión de una aplicación de consola de C# sencilla'
description: Aprenda a desarrollar una aplicación de consola de C# en Visual Studio mediante un procedimiento paso a paso.
ms.custom: get-started
ms.date: 07/09/2020
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: ghogen
ms.author: ghogen
manager: jmartens
monikerRange: '>=vs-2019'
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e5552cc3d84eb0dd2a44943c36ddaa60c827ceb6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99909324"
---
# <a name="tutorial-extend-a-simple-c-console-app"></a>Tutorial: Extensión de una aplicación de consola de C# sencilla

En este tutorial, aprenderá a usar Visual Studio para extender la aplicación de consola que creó en la primera parte. Conocerá algunas de las características de Visual Studio que necesitará para el desarrollo diario, como administrar varios proyectos y hacer referencia a paquetes de terceros.

Si acaba de completar la [primera parte](tutorial-console.md) de esta serie, ya tiene la aplicación de consola de calculadora.  Para omitir la parte 1, abra el proyecto desde un repositorio de GitHub. La aplicación de calculadora de C# está en el [repositorio vs-tutorial-samples](https://github.com/MicrosoftDocs/vs-tutorial-samples), por lo que solo tiene que seguir los pasos que se describen en [Tutorial: Abrir un proyecto desde un repositorio](../tutorial-open-project-from-repo.md) para empezar.

## <a name="add-a-new-project"></a>Incorporación de proyecto nuevo

El código real está formado por numerosos proyectos que funcionan conjuntamente para dar lugar a una solución. Ahora, vamos a agregar otro proyecto a la aplicación de calculadora. Consiste en una biblioteca de clases que proporciona algunas de las funciones de la calculadora.

1. En Visual Studio, puede usar el comando del menú de nivel superior **Archivo** > **Agregar** > **Nuevo proyecto** para agregar un proyecto nuevo. También puede hacer clic con el botón derecho en el nombre del proyecto existente (denominado "nodo del proyecto") y abrir el menú contextual del proyecto. Este menú contextual contiene muchas maneras de agregar funcionalidad a los proyectos. Así pues, haga clic con el botón derecho en el nodo del proyecto en el **Explorador de soluciones** y seleccione **Agregar** > **Nuevo proyecto**.

1. Seleccione la plantilla de proyecto de C# **Biblioteca de clases (.NET Standard)** .

   ![Captura de pantalla de la selección de la plantilla de proyecto Biblioteca de clases](media/vs-2019/calculator2-add-project-dark.png)

1. Escriba el nombre del proyecto **CalculatorLibrary** y seleccione **Crear**. Visual Studio crea el proyecto y lo agrega a la solución.

   ![Captura de pantalla del Explorador de soluciones con el proyecto de biblioteca de clases CalculatorLibrary agregado](media/vs-2019/calculator2-solution-explorer-with-class-library-dark2.png)

1. En lugar de dejar el nombre de archivo *Class1.cs*, cámbielo a **CalculatorLibrary.cs**. Puede hacer clic en el nombre en el **Explorador de soluciones** para cambiarlo, o bien hacer clic con el botón derecho y seleccionar **Cambiar nombre**. Otra opción es presionar la tecla **F2**.

   Es posible que se le pregunte si quiere cambiar el nombre de las referencias a `Class1` en el archivo. No importa qué responda en este momento, ya que reemplazará el código en un paso posterior.

1. Ahora debemos agregar una referencia de proyecto para que el primer proyecto pueda usar las API que expone la nueva biblioteca de clases.  Haga clic con el botón derecho en el nodo **Referencias** del primer proyecto y seleccione **Agregar referencia de proyecto**.

   ![Captura de pantalla del elemento de menú Agregar referencia de proyecto](media/vs-2019/calculator2-add-project-reference-dark.png)

   Aparecerá el cuadro de diálogo **Administrador de referencias**. Este cuadro de diálogo permite agregar referencias a otros proyectos, así como los ensamblados y las DLL COM que los proyectos necesiten.

   ![Captura de pantalla del cuadro de diálogo Administrador de referencias](media/vs-2019/calculator2-ref-manager-dark.png)

1. En el cuadro de diálogo **Administrador de referencias**, active la casilla correspondiente al proyecto **CalculatorLibrary** y seleccione **Aceptar**.  La referencia del proyecto aparece en un nodo **Proyectos** en el **Explorador de soluciones**.

   ![Captura de pantalla del Explorador de soluciones con una referencia de proyecto](media/vs-2019/calculator2-solution-explorer-with-project-reference-dark2.png)

1. En *Program.cs*, seleccione la clase `Calculator` y todo su código, y presione **CTRL+X** para cortarla de Program.cs. Después, en **CalculatorLibrary**, en *CalculatorLibrary.cs*, pegue el código en el espacio de nombres `CalculatorLibrary`. Posteriormente, haga que la clase Calculator `public` lo exponga fuera de la biblioteca. El código de *CalculatorLibrary.cs* ahora debería ser similar al siguiente:

   ```csharp
   using System;

    namespace CalculatorLibrary
    {
        public class Calculator
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
    }
   ```

1. El primer proyecto tiene una referencia, pero verá un error que la llamada a Calculator.DoOperation no resuelve. Esto se debe a que CalculatorLibrary está en un espacio de nombres diferente, por lo que debe agregar el espacio de nombres `CalculatorLibrary` para obtener una referencia completa.

   ```csharp
   result = CalculatorLibrary.Calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

   Pruebe a agregar una directiva using al principio del archivo:

   ```csharp
   using CalculatorLibrary;
   ```

   Este cambio debería permitirle quitar el espacio de nombres CalculatorLibrary del sitio de llamada, pero ahora hay una ambigüedad. ¿Es `Calculator` la clase de CalculatorLibrary, o es Calculator el espacio de nombres?  Para resolver la ambigüedad, cambie el nombre del espacio de nombres a `CalculatorProgram`.

   ```csharp
   namespace CalculatorProgram
   ```

## <a name="reference-net-libraries-write-to-a-log"></a>Referencia a bibliotecas de .NET: escritura en un registro

1. Supongamos que ahora quiere agregar un registro de todas las operaciones y escribirlo en un archivo de texto. La clase `Trace` de .NET proporciona esta funcionalidad. (También es útil para las técnicas básicas de impresión de la depuración).  La clase Trace se encuentra en System.Diagnostics, y se necesitan clases System.IO como `StreamWriter`, así que empiece por agregar las directivas Using:

   ```csharp
   using System.IO;
   using System.Diagnostics;
   ```

1. Si observa cómo se usa la clase Trace, es necesario mantener una referencia para la clase, que está asociada a una secuencia de archivos. Esto significa que la calculadora funcionaría mejor como un objeto, por lo que vamos a agregar un constructor.

   ```csharp
   public Calculator()
        {
            StreamWriter logFile = File.CreateText("calculator.log");
            Trace.Listeners.Add(new TextWriterTraceListener(logFile));
            Trace.AutoFlush = true;
            Trace.WriteLine("Starting Calculator Log");
            Trace.WriteLine(String.Format("Started {0}", System.DateTime.Now.ToString()));
        }

    public double DoOperation(double num1, double num2, string op)
        {
   ```

1. Además, hay que cambiar el método `DoOperation` estático a un método de miembro.  Vamos a agregar también una salida a cada cálculo para el registro, de modo que DoOperation tendrá un aspecto similar al del código siguiente:

   ```csharp
   public double DoOperation(double num1, double num2, string op)
   {
        double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.

        // Use a switch statement to do the math.
        switch (op)
        {
            case "a":
                result = num1 + num2;
                Trace.WriteLine(String.Format("{0} + {1} = {2}", num1, num2, result));
                break;
            case "s":
                result = num1 - num2;
                Trace.WriteLine(String.Format("{0} - {1} = {2}", num1, num2, result));
                break;
            case "m":
                result = num1 * num2;
                Trace.WriteLine(String.Format("{0} * {1} = {2}", num1, num2, result));
                break;
            case "d":
                // Ask the user to enter a non-zero divisor.
                if (num2 != 0)
                {
                    result = num1 / num2;
                    Trace.WriteLine(String.Format("{0} / {1} = {2}", num1, num2, result));
                }
                    break;
            // Return text for an incorrect option entry.
            default:
                break;
        }
        return result;
    }
   ```

1. Ahora, de nuevo en Program.cs, la llamada estática está marcada con una línea ondulada roja. Para corregirlo, cree una variable `calculator` mediante la incorporación de la línea siguiente justo antes del bucle while:

   ```csharp
   Calculator calculator = new Calculator();
   ```

   Modifique el sitio de llamada para `DoOperation` como se indica a continuación:

   ```csharp
   result = calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

1. Vuelva a ejecutar el programa y, cuando haya terminado, haga clic con el botón derecho en el nodo del proyecto y elija **Abrir la carpeta en el Explorador de archivos**. Luego, desplácese hacia abajo en el Explorador de archivos a la carpeta de salida. Podría ser *bin/Debug/netcoreapp3.1*. Abra el archivo *calculator.log*.

    ```output
    Starting Calculator Log
    Started 7/9/2020 1:58:19 PM
    1 + 2 = 3
    3 * 3 = 9
    ```

## <a name="add-a-nuget-package-write-to-a-json-file"></a>Incorporación de paquete NuGet: escritura en un archivo JSON

1. Supongamos ahora que queremos generar las operaciones en JSON, un formato popular y portable para almacenar datos de objeto. Para implementar esta funcionalidad, es necesario hacer referencia al paquete NuGet Newtonsoft.Json. Los paquetes NuGet son el vehículo principal para la distribución de bibliotecas de clases .NET. En el **Explorador de soluciones**, haga clic con el botón derecho en el nodo **Referencias** del proyecto CalculatorLibrary y seleccione **Administrar paquetes NuGet**.

   ![Captura de pantalla del menú contextual Administrar paquetes NuGet](media/vs-2019/calculator2-manage-nuget-packages-dark2.png)

   Se abrirá el administrador de paquetes NuGet.

   ![Captura de pantalla del Administrador de paquetes NuGet](media/vs-2019/calculator2-nuget-package-manager-dark.png)

1. Busque el paquete Newtonsoft.Json y seleccione **Instalar**.

   ![Captura de pantalla de la información del paquete NuGet Newtonsoft](media/vs-2019/calculator2-nuget-newtonsoft-json-dark2.png)

   El paquete se descarga, se agrega al proyecto y aparece una nueva entrada en el nodo Referencias del **Explorador de soluciones**.

1. Agregue una directiva Using del paquete System.IO y Newtonsoft.Json al principio de *CalculatorLibrary.cs*.

   ```csharp
   using Newtonsoft.Json;
   ```

1. Ahora, reemplace el constructor para Calculator por el código siguiente y cree el objeto de miembro JsonWriter:

   ```csharp
        JsonWriter writer;

        public Calculator()
        {
            StreamWriter logFile = File.CreateText("calculatorlog.json");
            logFile.AutoFlush = true;
            writer = new JsonTextWriter(logFile);
            writer.Formatting = Formatting.Indented;
            writer.WriteStartObject();
            writer.WritePropertyName("Operations");
            writer.WriteStartArray();
        }
   ```

1. Modifique el método `DoOperation` para agregar el código del escritor de JSON:

   ```csharp
        public double DoOperation(double num1, double num2, string op)
        {
            double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.
            writer.WriteStartObject();
            writer.WritePropertyName("Operand1");
            writer.WriteValue(num1);
            writer.WritePropertyName("Operand2");
            writer.WriteValue(num2);
            writer.WritePropertyName("Operation");
            // Use a switch statement to do the math.
            switch (op)
            {
                case "a":
                    result = num1 + num2;
                    writer.WriteValue("Add");
                    break;
                case "s":
                    result = num1 - num2;
                    writer.WriteValue("Subtract");
                    break;
                case "m":
                    result = num1 * num2;
                    writer.WriteValue("Multiply");
                    break;
                case "d":
                    // Ask the user to enter a non-zero divisor.
                    if (num2 != 0)
                    {
                        result = num1 / num2;
                        writer.WriteValue("Divide");
                    }
                    break;
                // Return text for an incorrect option entry.
                default:
                    break;
            }
            writer.WritePropertyName("Result");
            writer.WriteValue(result);
            writer.WriteEndObject();

            return result;
        }
   ```

1. Deberá agregar un método para finalizar la sintaxis JSON una vez que el usuario haya acabado de escribir los datos de la operación.

   ```csharp
    public void Finish()
    {
        writer.WriteEndArray();
        writer.WriteEndObject();
        writer.Close();
    }
   ```

1. En *Program.cs*, agregue una llamada a Finish al final.

   ```csharp
            // And call to close the JSON writer before return
            calculator.Finish();
            return;
        }
   ```

1. Compile y ejecute la aplicación y, cuando acabe de escribir algunas operaciones, cierre la aplicación correctamente con el comando "n".  Ahora abra el archivo calculatorlog.json. Debería ver algo parecido a lo siguiente:

   ```json
   {
    "Operations": [
        {
        "Operand1": 2.0,
        "Operand2": 3.0,
        "Operation": "Add",
        "Result": 5.0
        },
        {
        "Operand1": 3.0,
        "Operand2": 4.0,
        "Operation": "Multiply",
        "Result": 12.0
        }
    ]
   }
   ```

## <a name="debug-set-and-hit-a-breakpoint"></a>Depuración: establecimiento y uso de los puntos de interrupción

El depurador de Visual Studio es una herramienta eficaz que permite ejecutar el código paso a paso para buscar el punto exacto donde se ha cometido un error de programación. A continuación, comprenderá qué correcciones necesita hacer en el código. Visual Studio le permite realizar cambios temporales para poder seguir ejecutando el programa.

1. En *Program.cs*, haga clic en el margen situado a la izquierda del código siguiente (o bien, abra el menú contextual y elija **Punto de interrupción** > **Insertar punto de interrupción** o presione **F9**):

   ```csharp
   result = calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

   El círculo rojo que aparece indica un punto de interrupción. Puede usar puntos de interrupción para pausar la aplicación e inspeccionar el código. Puede establecer un punto de interrupción en cualquier línea de código ejecutable.

   ![Captura de pantalla del establecimiento de un punto de interrupción](media/vs-2019/calculator-2-debug-set-breakpoint.png)

1. Compile y ejecute la aplicación.

1. En la aplicación en ejecución, escriba algunos valores para el cálculo:

   - Para el primer número, escriba **8** e introdúzcalo.
   - Para el segundo número, escriba **0** e introdúzcalo.
   - Para el operador, divirtámonos; escriba **d** e introdúzcalo.

   La aplicación se suspende en el punto en el que creó el punto de interrupción, que se indica mediante el puntero amarillo de la izquierda y el código resaltado. El código resaltado todavía no se ha ejecutado.

   ![Captura de pantalla de la llegada a un punto de interrupción](media/vs-2019/calculator-2-debug-hit-breakpoint.png)

   Ahora, con la aplicación suspendida, puede inspeccionar el estado de la aplicación.

## <a name="debug-view-variables"></a>Depuración: ver variables

1. En el código resaltado, mantenga el puntero sobre variables como `cleanNum1` y `op`. Verá los valores actuales de estas variables (`8` y `d`, respectivamente), que aparecen en DataTips.

   ![Captura de pantalla de visualización de un DataTip](media/vs-2019/calculator-2-debug-view-datatip.png)

   Durante la depuración, la comprobación de si las variables contienen los valores que espera que contengan suele ser fundamental para corregir los problemas.

2. En el panel inferior, examine la ventana **Variables locales**. (Si está cerrada, elija **Depurar** > **Ventanas** > **Variables locales** para abrirla).

   En la ventana Variables locales, verá cada variable que está actualmente en el ámbito, junto con su valor y tipo.

   ![Captura de pantalla de la ventana Variables locales](media/vs-2019/calculator-2-debug-locals-window.png)

3. Fíjese en la ventana **Automático**.

   La ventana Automático es similar a la ventana **Variables locales**, pero muestra las variables inmediatamente anteriores y posteriores a la línea de código actual en la que la aplicación permanece en pausa.

   A continuación, ejecutará el código en el depurador instrucción por instrucción, lo que se denomina *ejecución paso a paso*.

## <a name="debug-step-through-code"></a>Depuración: examinar el código

1. Presione **F11** (o **Depurar** > **Depurar paso a paso por instrucciones**).

   Con el comando Depurar paso a paso por instrucciones, la aplicación ejecuta la instrucción actual y avanza hasta la siguiente instrucción ejecutable (normalmente la siguiente línea de código). El puntero amarillo de la izquierda siempre indica la instrucción actual.

   ![Captura de pantalla del comando Depurar paso a paso por instrucciones](media/vs-2019/calculator-2-debug-step-into.png)

   Acaba de depurar paso a paso por instrucciones el método `DoOperation` de la clase `Calculator`.

1. Para obtener una visión jerárquica del flujo del programa, examine la ventana **Pila de llamadas**. (Si está cerrada, elija **Depurar** > **Ventanas** > **Pila de llamadas**).

   ![Captura de pantalla de la pila de llamadas](media/vs-2019/calculator-2-debug-call-stack.png)

   Esta vista muestra el método `Calculator.DoOperation` actual, indicado por el puntero amarillo, y la segunda fila muestra la función que lo llamó, del método `Main` en *Program.cs*. En la ventana **Pila de llamadas** se muestra el orden en el que se llama a los métodos y las funciones. Además, proporciona acceso a muchas características del depurador, como **Ir al código fuente**, en el menú contextual.

1. Presione **F10** (o **Depurar** > **Depurar paso a paso por procedimientos**) varias veces hasta que la aplicación se pause en la instrucción `switch`.

   ```csharp
   switch (op)
   {
   ```

   El comando Depurar paso a paso por procedimientos es similar al comando Depurar paso a paso por instrucciones, salvo que si la instrucción actual llama a una función, el depurador ejecuta el código de la función llamada y no suspende la ejecución hasta que la función vuelve. Depurar paso a paso por procedimientos es una forma más rápida de navegar por el código si no está interesado en una función determinada.

1. Presione **F10** una vez más para que la aplicación se pause en la siguiente línea de código.

   ```csharp
   if (num2 != 0)
   {
   ```

   Este código comprueba si hay un caso de división por cero. Si la aplicación continúa, iniciará una excepción general (un error), pero supongamos que lo considera un error y quiere hacer algo más, como ver el valor devuelto real en la consola. Una opción consiste en usar una característica del depurador denominada Editar y continuar para realizar cambios en el código y luego seguir con la depuración. Sin embargo, le mostraremos un truco diferente para modificar temporalmente el flujo de ejecución.

## <a name="debug-test-a-temporary-change"></a>Depuración: probar un cambio temporal

1. Seleccione el puntero amarillo, actualmente en pausa en la instrucción `if (num2 != 0)`, y arrástrelo a la siguiente instrucción.

   ```csharp
   result = num1 / num2;
   ```

   Al hacerlo, la aplicación omite completamente la instrucción `if`, por lo que puede ver lo que sucede cuando se divide por cero.

1. Presione **F10** para ejecutar la línea de código.

1. Mantenga el puntero sobre la variable `result` y verá que almacena un valor de `Infinity`.

   En C#, `Infinity` es el resultado de dividir por cero.

1. Presione **F5** (o, **Depurar** > **Continuar depurando**).

   El símbolo de infinito aparece en la consola como el resultado de la operación matemática.

1. Cierre la aplicación correctamente con el comando "n".

## <a name="next-steps"></a>Pasos siguientes

Enhorabuena por completar este tutorial. Para más información, continúe con los tutoriales siguientes.

> [!div class="nextstepaction"]
> [Continuar con más tutoriales de C#](/dotnet/csharp/tutorials/)

> [!div class="nextstepaction"]
> [Continuar con la introducción al IDE de Visual Studio](/../visual-studio-ide.md)

## <a name="see-also"></a>Vea también

* [IntelliSense para C#](../../ide/visual-csharp-intellisense.md)
* [Información sobre cómo depurar código de C# con Visual Studio](tutorial-debugger.md)
