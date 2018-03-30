---
title: Depurar con código administrado mediante el depurador de Visual Studio | Documentos de Microsoft
ms.custom: mvc
ms.date: 03/18/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: f4cea2e1-08dc-47ac-aba2-3b8c338e607f
caps.latest.revision: 1
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: e44cf8d282c253da7fa3a09ed8d3b90ca46ca07a
ms.sourcegitcommit: 064f8678f4a918e1dce60285090a9803d37dc34b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/30/2018
---
# <a name="debug-with-managed-code-using-the-visual-studio-debugger"></a>Depurar con código administrado mediante el depurador de Visual Studio

El depurador de Visual Studio proporciona muchas características eficaces para ayudarle a depurar sus aplicaciones. En este tema se proporciona una forma rápida de obtener información sobre las características básicas.

## <a name="create-a-new-project"></a>Crear un proyecto nuevo 

1. En Visual Studio, seleccione **Archivo > Nuevo proyecto**.

2. En **Visual C#** o **Visual Basic**, elija **.NET Core**y, a continuación, en el panel central, elija **aplicación de consola (.NET Core)**.

     Si no ve la plantilla de proyecto **Aplicación de consola (.NET Core)**, haga clic en el vínculo **Abrir el instalador de Visual Studio** en el panel izquierdo del cuadro de diálogo **Nuevo proyecto**. Se iniciará el Instalador de Visual Studio. Elija la **desarrollo de escritorio de .NET** y **.NET Core** carga de trabajo, a continuación, elija **modificar**.

3. Escriba un nombre como **MyDbgApp** y haga clic en **Aceptar**.

    Visual Studio crea el proyecto.

4. En Program.cs o Module1.vb, reemplace el código siguiente

    ```c#
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

    ```c#
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
    > En Visual Basic, asegúrese de que el objeto de inicio se establece en `Sub Main` (**Propiedades > Aplicaciones > Objeto de inicio**).

## <a name="set-a-breakpoint"></a>Establecer un punto de interrupción

A *punto de interrupción* es un marcador que indica dónde Visual Studio debe suspender la ejecución de código para poder echar un vistazo a los valores de variables o el comportamiento de la memoria, o si tiene o no una bifurcación del código que está ejecutando. Es la característica más básica en la depuración.

1. Para establecer el punto de interrupción, haga clic en el margen interno a la izquierda de la `doWork` llamada de función (o seleccione la línea de código y presione **F9**).

    ![Establecer un punto de interrupción](../debugger/media/dbg-qs-set-breakpoint-csharp.png "establecer un punto de interrupción")

2. Presione ahora **F5** (o elija **Depurar > Iniciar depuración**).

    ![Alcanza un punto de interrupción](../debugger/media/dbg-qs-hit-breakpoint-csharp.png "alcanza un punto de interrupción")

    El depurador realiza una pausa en la que estableció el punto de interrupción. La instrucción donde se pausó la ejecución del depurador y la aplicación se indica mediante la flecha amarilla. La línea con la `doWork` aún no se ha ejecutado la llamada de función.

    > [!TIP]
    > Si tiene un punto de interrupción en un bucle o recursividad, o si tiene muchos puntos de interrupción que con frecuencia recorre paso a paso, use un [punto de interrupción condicional](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) para asegurarse de que el código se suspende únicamente cuando se cumplen determinadas condiciones. Un punto de interrupción condicional puede ahorrar tiempo y también facilitan depurar los problemas que son difíciles de reproducir.

## <a name="navigate-code"></a>Navegación en el código

Hay comandos diferentes para indicar al depurador para continuar. Se muestra un comando de exploración de código de utilidad que es nuevo en Visual Studio de 2017.

Mientras está en pausa en el punto de interrupción, mantenga el mouse sobre la instrucción `c1.AddLast(20)` hasta que el verde **ejecutar hasta que haga clic en** botón ![ejecutar, haga clic en](../debugger/media/dbg-tour-run-to-click.png "RunToClick") aparece y, a continuación, presione la **Ejecutar hasta que haga clic en** botón.

![Ejecutar hasta que haga clic en](../debugger/media/dbg-qs-run-to-click-csharp.png "ejecución hacer clic en")

La aplicación continúa la ejecución, una llamada a `doWork`y se detiene en la línea de código donde se ha hecho clic el botón.

Comandos de teclado comunes que permiten recorrer el código incluyen **F10** y **F11**. Para obtener instrucciones más detalladas, consulte el [guía para principiantes](../debugger/getting-started-with-the-debugger.md).

## <a name="inspect-variables-in-a-datatip"></a>Inspeccionar las variables en una información sobre datos

1. En la línea actual de código (marcado con el puntero de ejecución amarillo), mantenga el mouse sobre el `c1` objeto con el mouse para mostrar una información sobre datos.

    ![Ver una información sobre datos](../debugger/media/dbg-qs-data-tip-csharp.png "ver una información sobre datos")

    La información sobre datos muestra el valor actual de la `c1` variable y le permite inspeccionar sus propiedades. Al depurar, si ve un valor que no esperaba, probablemente tenga un error en las líneas de código anteriores o que realiza la llamada. 

2. Expanda la información sobre datos para buscar en los valores de propiedad actuales de la `c1` objeto.

3. Si desea anclar la información sobre datos para que pueda continuar ver el valor de `c1` mientras se ejecuta el código, haga clic en el icono de anclaje pequeño. (Puede mover la información sobre datos a una ubicación adecuada).

## <a name="edit-code-and-continue-debugging"></a>Editar código y continuar con la depuración

Si se identifica un cambio que desea probar en el código durante una sesión de depuración, puede hacerlo, demasiado.

1. Haga clic en la segunda instancia de `c2.First.Value` y cambiar `c2.First.Value` a `c2.Last.Value`.

2. Presione **F10** (o **Depurar > paso a paso por**) pocas veces para avanzar el depurador y ejecutar el código revisado.

    ![Editar y continuar](../debugger/media/dbg-qs-edit-and-continue-csharp.gif "editar y continuar")

    **F10** hace avanzar la instrucción de depurador uno en uno, pero pasos sobre las funciones en lugar de ejecución paso a paso en ellos (que omita aún se ejecuta el código).

Para obtener más información sobre el uso de editar y continuar y las limitaciones de características, vea [editar y continuar](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Pasos siguientes

En este tutorial, ha aprendido cómo iniciar al depurador, recorrer el código e inspeccionar las variables. Puede obtener una visión general de las características del depurador junto con vínculos a más información.

> [!div class="nextstepaction"]
> [Guía de características del depurador](../debugger/debugger-feature-tour.md)
