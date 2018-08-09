---
title: Depurar código administrado | Microsoft Docs
description: Depuración de C# o Visual Basic con el depurador de Visual Studio
ms.custom: mvc
ms.date: 03/18/2018
ms.technology: vs-ide-debug
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: f4cea2e1-08dc-47ac-aba2-3b8c338e607f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 2ba06156a8fa44a61b489deba6104673e8fb08ce
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39637528"
---
# <a name="quickstart-debug-with-managed-code-using-the-visual-studio-debugger"></a>Inicio rápido: Depurar con código administrado mediante el depurador de Visual Studio

El depurador de Visual Studio proporciona muchas características eficaces para ayudarle a depurar sus aplicaciones. En este tema se proporciona una forma rápida de obtener información sobre las características básicas.

## <a name="create-a-new-project"></a>Crear un proyecto nuevo 

1. En Visual Studio, seleccione **Archivo > Nuevo proyecto**.

2. En **Visual C#** o **Visual Basic**, elija **.NET Core**y, a continuación, en el panel central, elija **aplicación de consola (.NET Core)**.

     Si no ve la plantilla de proyecto **Aplicación de consola (.NET Core)**, haga clic en el vínculo **Abrir el instalador de Visual Studio** en el panel izquierdo del cuadro de diálogo **Nuevo proyecto**. Se iniciará el Instalador de Visual Studio. Elija la **desarrollo de escritorio de .NET** y **.NET Core** carga de trabajo, a continuación, elija **modificar**.

3. Escriba un nombre como **MyDbgApp** y haga clic en **Aceptar**.

    Visual Studio crea el proyecto.

4. En *Program.cs* o *Module1.vb*, reemplace el código siguiente

    ```csharp
    class Program
    {
        static void Main(string[] args)
        {
        }
    }
    ```

    ```vb
    Module Module1
        Sub Main()
        End Sub
    End Module
    ```

    con este código:

    ```csharp
    class Program
    {
        private static void doWork()
        {
            LinkedList<int> c1 = new LinkedList<int>();

            c1.AddLast(10);
            c1.AddLast(20);

            LinkedList<int> c2 = new LinkedList<int>(c1);
            int i = c2.First.Value;
            int j = c2.First.Value;
            Console.Write("The first element is ");
            Console.Write(i);
            Console.Write("\n");
            Console.Write("The second element is ");
            Console.Write(j);
            Console.Write("\n");

        }

        static int Main()
        {
            // using namespace std;
            doWork();
            return 0;

        }
    }
    ```

    ```vb
    Imports System.Collections.Generic

    Namespace MyDbgApp
        Class Program
            Private Shared Sub doWork()
                Dim c1 As New LinkedList(Of Integer)()

                c1.AddLast(10)
                c1.AddLast(20)

                Dim c2 As New LinkedList(Of Integer)(c1)
                Dim i As Integer = c2.First.Value
                Dim j As Integer = c2.First.Value
                Console.Write("The first element is ")
                Console.Write(i)
                Console.Write(vbLf)
                Console.Write("The second element is ")
                Console.Write(j)
                Console.Write(vbLf)

            End Sub

            Public Shared Function Main() As Integer
                ' using namespace std;
                doWork()
                Return 0

            End Function
        End Class
    End Namespace
    ```

    > [!NOTE]
    > En Visual Basic, asegúrese de que el objeto de inicio se establece en `Sub Main` (**Propiedades &gt; Aplicaciones &gt; Objeto de inicio**).

## <a name="set-a-breakpoint"></a>Establecer un punto de interrupción

Un *punto de interrupción* es un marcador que indica dónde Visual Studio debe suspender la ejecución de código para que pueda sacar un vistazo a los valores de variables o el comportamiento de la memoria o si no está ejecutando una bifurcación de código. Es la característica más básica en la depuración.

1. Para establecer el punto de interrupción, haga clic en el margen interno a la izquierda de la `doWork` llamada de función (o seleccione la línea de código y presione **F9**).

    ![Establezca un punto de interrupción](../debugger/media/dbg-qs-set-breakpoint-csharp.png "establecer un punto de interrupción")

2. Ahora presione **F5** (o elija **Depurar > Iniciar depuración**).

    ![Alcanzar un punto de interrupción](../debugger/media/dbg-qs-hit-breakpoint-csharp.png "alcanza un punto de interrupción")

    El depurador realiza una pausa donde estableció el punto de interrupción. La instrucción donde se detuvo la ejecución del depurador y la aplicación se indica mediante la flecha amarilla. La línea con el `doWork` aún no se ha ejecutado la llamada de función.

    > [!TIP]
    > Si tiene un punto de interrupción en un bucle o recursividad, o si tiene muchos puntos de interrupción que con frecuencia paso a paso, use un [punto de interrupción condicional](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) para asegurarse de que el código se suspende únicamente cuando se cumplen determinadas condiciones. Un punto de interrupción condicional puede ahorrar tiempo y también resultará más fácil depurar los problemas que son difíciles de reproducir.

## <a name="navigate-code"></a>Navegación en el código

Hay comandos diferentes para indicar al depurador para continuar. Se muestra un comando de navegación de código útil que es nuevo en Visual Studio 2017.

Mientras está en pausa en el punto de interrupción, mantenga el mouse sobre la instrucción `c1.AddLast(20)` hasta que el verde **para ejecutar hasta** botón ![hacer clic y ejecutar](../debugger/media/dbg-tour-run-to-click.png "RunToClick") aparece y, a continuación, presione el **Para ejecutar hasta** botón.

![Para ejecutar hasta](../debugger/media/dbg-qs-run-to-click-csharp.png "para ejecutar hasta")

La aplicación sigue en ejecución, una llamada a `doWork`y se detiene en la línea de código donde hizo clic en el botón.

Comandos de teclado comunes utilizados para recorrer el código incluyen **F10** y **F11**. Para obtener más instrucciones, consulte el [guía para principiantes](../debugger/getting-started-with-the-debugger.md).

## <a name="inspect-variables-in-a-datatip"></a>Inspeccionar las variables en una información sobre datos

1. En la línea actual del código (marcado con el puntero de ejecución amarillo), mantenga el mouse sobre el `c1` objeto con el mouse para mostrar una información sobre datos.

    ![Ver una información sobre datos](../debugger/media/dbg-qs-data-tip-csharp.png "ver una información sobre datos")

    La información sobre datos muestra el valor actual de la `c1` variable y le permite inspeccionar sus propiedades. Al depurar, si ve un valor que no esperaba, probablemente tenga un error en las líneas de código anteriores o que realiza la llamada. 

2. Expanda la información sobre datos para observar los valores de propiedad actuales de la `c1` objeto.

3. Si desea anclar la información sobre datos para que pueda continuar ver el valor de `c1` mientras ejecuta código, haga clic en el icono de anclaje pequeño. (Puede mover la información sobre datos anclada a una ubicación adecuada).

## <a name="edit-code-and-continue-debugging"></a>Editar código y seguir depurando

Si identifica un cambio que se va a probar en el código en el transcurso de una sesión de depuración, puede hacer eso, demasiado.

1. Haga clic en la segunda instancia de `c2.First.Value` y cambiar `c2.First.Value` a `c2.Last.Value`.

2. Presione **F10** (o **Depurar > saltar**) varias veces para avanzar el depurador y ejecutar el código editado.

    ![Editar y continuar](../debugger/media/dbg-qs-edit-and-continue-csharp.gif "editar y continuar")

    **F10** hace avanzar la instrucción de depurador uno en un momento, pero los pasos a través de funciones en lugar de entrar en ellos (todavía se ejecuta el código que se omite).

Para obtener más información sobre el uso de editar y continuar y las limitaciones de características, consulte [editar y continuar](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Pasos siguientes

En este tutorial, ha aprendido cómo iniciar al depurador, paso a través del código e inspeccionar las variables. Es posible que desee obtener un alto nivel sobre las características del depurador junto con vínculos para obtener más información.

> [!div class="nextstepaction"]
> [Guía de características del depurador](../debugger/debugger-feature-tour.md)
