---
title: Depurar código administrado | Microsoft Docs
description: Depure C++ o Visual Basic mediante el depurador de Visual Studio
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
ms.openlocfilehash: e35d102a30ffc7b80d39f359542bbdc4c00feff6
ms.sourcegitcommit: a7de99f36e9ead7ea9e9bac23c88d05ddfc38b00
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2018
ms.locfileid: "52257191"
---
# <a name="quickstart-debug-with-c-or-visual-basic-using-the-visual-studio-debugger"></a>Inicio rápido: Depurar con C# o Visual Basic mediante el depurador de Visual Studio

El depurador de Visual Studio proporciona muchas características de gran eficacia para ayudar a depurar aplicaciones. En este tema se proporciona una forma rápida de obtener información sobre las características básicas.

## <a name="create-a-new-project"></a>Crear un proyecto nuevo 

1. En Visual Studio, seleccione **Archivo > Nuevo proyecto**.

2. En **Visual C#** o **Visual Basic**, elija **.NET Core** y, después, en el panel central, elija **Aplicación de consola (.NET Core)**.

     Si no ve la plantilla de proyecto **Aplicación de consola (.NET Core)**, haga clic en el vínculo **Abrir el instalador de Visual Studio** en el panel izquierdo del cuadro de diálogo **Nuevo proyecto**. Se iniciará el Instalador de Visual Studio. Elija la carga de trabajo **Desarrollo de escritorio de .NET** y **.NET Core** y luego **Modificar**.

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

Un *punto de interrupción* es un marcador que indica en qué punto debe Visual Studio suspender la ejecución de código para poder echar un vistazo a los valores de variables, o al comportamiento de memoria, o si se está ejecutando o no una rama de código. Es la característica más básica de la depuración.

1. Para establecer el punto de interrupción, haga clic en el medianil de la izquierda de la llamada a la función `doWork` (o seleccione la línea de código y presione **F9**).

    ![Establecimiento de un punto de interrupción](../debugger/media/dbg-qs-set-breakpoint-csharp.png "Set a breakpoint")

2. Ahora presione **F5** (o elija **Depurar > Iniciar depuración**).

    ![Llegada a un punto de interrupción](../debugger/media/dbg-qs-hit-breakpoint-csharp.png "Hit a breakpoint")

    El depurador se detiene donde se ha establecido el punto de interrupción. La instrucción donde se ha detenido la ejecución del depurador y la aplicación se indica mediante la flecha amarilla. La línea con la llamada a la función `doWork` aún no se ha ejecutado.

    > [!TIP]
    > Si tiene un punto de interrupción en un bucle o recursión, o si tiene muchos puntos de interrupción que ejecuta paso a paso con frecuencia, use un [punto de interrupción condicional](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) para asegurarse de que el código se suspende ÚNICAMENTE cuando se cumplen determinadas condiciones. Un punto de interrupción condicional puede ahorrar tiempo y además puede facilitar la depuración de problemas que son difíciles de reproducir.

## <a name="navigate-code"></a>Navegación en el código

Hay distintos comandos para indicar al depurador que continúe. Aquí se muestra un útil comando de navegación de código que es nuevo en Visual Studio 2017.

Mientras la ejecución está detenida en el punto de interrupción, mantenga el puntero sobre la instrucción `c1.AddLast(20)` hasta que aparezca el botón verde **Run to click** (Ejecutar hasta clic) ![Ejecutar hasta clic](../debugger/media/dbg-tour-run-to-click.png "RunToClick") y luego presione el botón **Ejecutar hasta clic**.

![Ejecutar hasta clic](../debugger/media/dbg-qs-run-to-click-csharp.png "Run to click")

La aplicación se sigue ejecutando, llama a `doWork` y se detiene en la línea de código donde se ha hecho clic en el botón.

Los comandos de teclado habituales usados para ejecutar el código paso a paso son **F10** y **F11**. Para obtener más instrucciones detalladas, vea la [Guía para principiantes](../debugger/getting-started-with-the-debugger.md).

## <a name="inspect-variables-in-a-datatip"></a>Inspeccionar las variables de una información sobre datos

1. En la línea de código actual (marcada con el puntero de ejecución amarillo), mantenga el puntero sobre el objeto `c1` para mostrar una información sobre datos.

    ![Visualización de una información sobre datos](../debugger/media/dbg-qs-data-tip-csharp.png "View a datatip")

    La información sobre datos muestra el valor actual de la variable `c1` y permite inspeccionar sus propiedades. Al depurar, si ve un valor que no esperaba, probablemente tenga un error en las líneas de código anteriores o de llamada. 

2. Expanda la información sobre datos para ver los valores de propiedad actuales del objeto `c1`.

3. Si quiere anclar la información sobre datos para poder seguir viendo el valor de `c1` mientras ejecuta el código, haga clic en el icono de anclar pequeño. (Puede mover la información sobre datos anclada a una ubicación que le resulte cómoda).

## <a name="edit-code-and-continue-debugging"></a>Editar código y seguir depurando

Si identifica un cambio que quiere probar en el código a mitad de una sesión de depuración, también puede hacerlo.

1. Haga clic en la segunda instancia de `c2.First.Value` y cambie `c2.First.Value` por `c2.Last.Value`.

2. Presione **F10** (o **Depurar > Saltar**) varias veces para que el depurador avance y ejecute el código editado.

    ![Editar y continuar](../debugger/media/dbg-qs-edit-and-continue-csharp.gif "Edit and continue")

    **F10** hace que el depurador avance de instrucción en instrucción, pero que se salte las funciones en lugar de depurarlas (el código que se omite se sigue ejecutando).

Para obtener más información sobre el uso de Editar y continuar y las limitaciones de las características, vea [Editar y continuar](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Pasos siguientes

En este tutorial, ha aprendido a iniciar el depurador, a ejecutar el código paso a paso y a inspeccionar variables. Puede ser que le interese analizar las características del depurador con más detenimiento, así como consultar los vínculos disponibles con más información.

> [!div class="nextstepaction"]
> [Guía de características del depurador](../debugger/debugger-feature-tour.md)
