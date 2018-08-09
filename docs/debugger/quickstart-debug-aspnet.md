---
title: Depuración de ASP.NET
description: Depuración de ASP.NET con el depurador de Visual Studio
ms.custom: mvc
ms.date: 08/06/2018
ms.technology: vs-ide-debug
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: f4cea2e1-08dc-47ac-aba2-3b8c338e607f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 74671401b3e3eaeae5840110dfc37c926266f98a
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39636992"
---
# <a name="quickstart-debug-aspnet-with-the-visual-studio-debugger"></a>Inicio rápido: Depurar ASP.NET con el depurador de Visual Studio

El depurador de Visual Studio proporciona muchas características eficaces para ayudarle a depurar sus aplicaciones. En este tema se proporciona una forma rápida de obtener información sobre las características básicas.

## <a name="create-a-new-project"></a>Crear un proyecto nuevo 

1. En Visual Studio, seleccione **Archivo > Nuevo proyecto**.

1. En **Visual C#**, elija **Web**y, a continuación, en el panel central, elija **aplicación Web ASP.NET Core**.

1. Escriba un nombre como **MyDbgApp** y haga clic en **Aceptar**.

1. En el cuadro de diálogo que aparece, elija **aplicación Web** en el panel central y, a continuación, haga clic en **Aceptar**.

     Si no ve el **aplicación Web** plantilla de proyecto, haga clic en el **abrir Visual Studio Installer** vínculo en el panel izquierdo de la **nuevo proyecto** cuadro de diálogo. Se iniciará el Instalador de Visual Studio. Elija la carga de trabajo **Desarrollo de ASP.NET y web** y después elija **Modificar**.

    ![Elija una aplicación Web](../debugger/media/dbg-qs-aspnet-choose-web-app.png)

    Visual Studio crea el proyecto.

1. En el Explorador de soluciones, abra About.cshtml.cs (bajo Pages/About.cshtml) y reemplace el código siguiente

    ```csharp
    public void OnGet()
    {
        Message = "Your application description page.";
    }
    ```

    con este código:

    ```csharp
    public void OnGet()
    {
        LinkedList<int> result = doWork();
        Message = "Result of work: " + result.First.Value + ", " + result.First.Value;
    }

    private static LinkedList<int> doWork()
    {
        LinkedList<int> c1 = new LinkedList<int>();

        c1.AddLast(10);
        c1.AddLast(20);

        LinkedList<int> c2 = new LinkedList<int>(c1);

        return c2;

    }
    ```

## <a name="set-a-breakpoint"></a>Establecer un punto de interrupción

Un *punto de interrupción* es un marcador que indica dónde Visual Studio debe suspender la ejecución de código para que pueda sacar un vistazo a los valores de variables o el comportamiento de la memoria o si no está ejecutando una bifurcación de código. Es la característica más básica en la depuración.

1. Para establecer el punto de interrupción, haga clic en el margen interno a la izquierda de la `doWork` función (o seleccione la línea de código y presione **F9**).

    ![Establecer un punto de interrupción](../debugger/media/dbg-qs-set-breakpoint-aspnet.png)

    Se establece el punto de interrupción a la izquierda de la llave de apertura (`{`).

1. Ahora presione **F5** (o elija **Depurar > Iniciar depuración**).

1. Cuando se carga la página web, haga clic en el **sobre** vínculo en la parte superior de la página web.

    El depurador realiza una pausa donde estableció el punto de interrupción. La instrucción donde se detuvo la ejecución del depurador y la aplicación se indica mediante la flecha amarilla. La línea con la llave de apertura (`{`) después de la `doWork` declaración de función no se ha ejecutado.

    ![Llegar a un punto de interrupción](../debugger/media/dbg-qs-hit-breakpoint-aspnet.png)

    > [!TIP]
    > Si tiene un punto de interrupción en un bucle o recursividad, o si tiene muchos puntos de interrupción que con frecuencia paso a paso, use un [punto de interrupción condicional](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) para asegurarse de que el código se suspende únicamente cuando se cumplen determinadas condiciones. Esto ahorra tiempo y también resultará más fácil depurar los problemas que son difíciles de reproducir.

## <a name="navigate-code"></a>Navegación en el código

Hay comandos diferentes para indicar al depurador para continuar. Se muestra un comando de navegación de código útil que es nuevo en Visual Studio 2017.

Mientras está en pausa en el punto de interrupción, mantenga el mouse sobre la instrucción `return c2` hasta que el verde **para ejecutar hasta** botón ![hacer clic y ejecutar](../debugger/media/dbg-tour-run-to-click.png) aparece y, a continuación, presione el **para ejecutar hasta** botón.

![Para ejecutar hasta](../debugger/media/dbg-qs-run-to-click-aspnet.png)

La aplicación continúa la ejecución y se detiene en la línea de código donde hizo clic en el botón.

Comandos de teclado comunes utilizados para recorrer el código incluyen **F10** y **F11**. Para obtener más instrucciones, consulte el [guía para principiantes](../debugger/getting-started-with-the-debugger.md).

## <a name="inspect-variables-in-a-datatip"></a>Inspeccionar las variables en una información sobre datos

1. En la línea actual del código (marcado con el puntero de ejecución amarillo), mantenga el mouse sobre el `c2` objeto con el mouse para mostrar una información sobre datos.

    ![Ver una información sobre datos](../debugger/media/dbg-qs-data-tip-aspnet.png)

    La información sobre datos muestra el valor actual de la `c2` variable y le permite inspeccionar sus propiedades. Al depurar, si ve un valor que no esperaba, probablemente tenga un error en las líneas de código anteriores o que realiza la llamada. 

2. Expanda la información sobre datos para observar los valores de propiedad actuales de la `c2` objeto.

3. Si desea anclar la información sobre datos para que pueda continuar ver el valor de `c2` mientras ejecuta código, haga clic en el icono de anclaje pequeño. (Puede mover la información sobre datos anclada a una ubicación adecuada).

## <a name="edit-code-and-continue-debugging"></a>Editar código y seguir depurando

Si identifica un cambio que se va a probar en el código en el transcurso de una sesión de depuración, puede hacer eso, demasiado.

1. En el `OnGet` método, haga clic en la segunda instancia de `result.First.Value` y cambiar `result.First.Value` a `result.Last.Value`.

1. Presione **F10** (o **Depurar > saltar**) varias veces para avanzar el depurador y ejecutar el código editado.

    ![Editar y continuar](../debugger/media/dbg-qs-edit-and-continue-aspnet.png "editar y continuar")

    **F10** hace avanzar la instrucción de depurador uno en un momento, pero los pasos a través de funciones en lugar de entrar en ellos (todavía se ejecuta el código que se omite).

Para obtener más información sobre el uso de editar y continuar y las limitaciones de características, consulte [editar y continuar](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Pasos siguientes

En este tutorial, ha aprendido cómo iniciar al depurador, paso a través del código e inspeccionar las variables. Es posible que desee obtener un alto nivel sobre las características del depurador junto con vínculos para obtener más información.

> [!div class="nextstepaction"]
> [Guía de características del depurador](../debugger/debugger-feature-tour.md)
