---
title: "Depuración ASP.NET: Visual Studio | Documentos de Microsoft"
ms.custom: 
ms.date: 12/06/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: quickstart
helpviewer_keywords: debugger
ms.assetid: f4cea2e1-08dc-47ac-aba2-3b8c338e607f
caps.latest.revision: "1"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b0ba7735dd44d029889c57d151e6fba39ba7b2df
ms.sourcegitcommit: 64c7682ec3a2cbea684e716803398d4278b591d1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2017
---
# <a name="debug-aspnet-with-the-visual-studio-debugger"></a>Depuración en ASP.NET con el depurador de Visual Studio

El depurador de Visual Studio proporciona muchas características eficaces para ayudarle a depurar sus aplicaciones. En este tema se proporciona una forma rápida de obtener información acerca de las características básicas.

## <a name="create-a-new-project"></a>Crear un proyecto nuevo 

1. En Visual Studio, elija **archivo > Nuevo proyecto**.

1. En **Visual C#**, elija **Web**y, a continuación, en el panel central, elija **aplicación Web de ASP.NET Core**.

1. Escriba un nombre como **MyDbgApp** y haga clic en **Aceptar**.

1. En el cuadro de diálogo que aparece, elija **aplicación Web** en el panel central y, a continuación, haga clic en **Aceptar**.

     Si no ve el **aplicación Web** plantilla de proyecto, haga clic en el **abrir Visual Studio Installer** vínculo en el panel izquierdo de la **nuevo proyecto** cuadro de diálogo. Se iniciará el Instalador de Visual Studio. Elija la **ASP.NET** y **.NET Core** carga de trabajo, a continuación, elija **modificar**.

    ![Elija una aplicación Web](../debugger/media/dbg-qs-aspnet-choose-web-app.png)

    Visual Studio crea el proyecto.

1. En el Explorador de soluciones, abra About.cshtml.cs (en Pages/About.cshtml) y reemplace el código siguiente

    ```c#
    public void OnGet()
    {
        Message = "Your application description page.";
    }
    ```

    con este código:

    ```c#
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

A *punto de interrupción* es un marcador que indica dónde Visual Studio debe suspender la ejecución de código para poder echar un vistazo a los valores de variables o el comportamiento de la memoria, o si tiene o no una bifurcación del código que está ejecutando. Es la característica más básica en la depuración.

1. Para establecer el punto de interrupción, haga clic en el margen interno a la izquierda de la `doWork` función (o seleccione la línea de código y presione **F9**).

    ![Establecer un punto de interrupción](../debugger/media/dbg-qs-set-breakpoint-aspnet.png)

    El punto de interrupción se establece a la izquierda de la llave de apertura (`{`).

1. Presione ahora **F5** (o elija **Depurar > Iniciar depuración**).

1. Cuando se carga la página web, haga clic en el **sobre** vínculo en la parte superior de la página web.

    El depurador realiza una pausa en la que estableció el punto de interrupción. La instrucción donde se pausó la ejecución del depurador y la aplicación se indica mediante la flecha amarilla. La línea con la llave de apertura (`{`) después de la `doWork` declaración de función no se ha ejecutado todavía.

    ![Llegar a un punto de interrupción](../debugger/media/dbg-qs-hit-breakpoint-aspnet.png)

    > [!TIP]
    > Si tiene un punto de interrupción en un bucle o recursividad, o si tiene una gran cantidad de puntos de interrupción que con frecuencia recorre paso a paso, use un [punto de interrupción condicional](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) para asegurarse de que el código se suspende únicamente cuando se cumplen determinadas condiciones. Esto ahorra tiempo y también resultará más fácil de depurar problemas que son difíciles de reproducir.

## <a name="navigate-code"></a>Navegar por el código

Hay comandos diferentes para indicar al depurador para continuar. Le mostraremos un comando de exploración de código de utilidad que es nuevo en Visual Studio de 2017.

- Mientras está en pausa en el punto de interrupción, mantenga el mouse sobre la instrucción `return c2` hasta que el verde **ejecutar hasta que haga clic en** botón ![ejecutar, haga clic en](../debugger/media/dbg-tour-run-to-click.png) aparece y, a continuación, presione la **ejecutar hasta que haga clic en** botón.

    ![Ejecutar hasta que haga clic en](../debugger/media/dbg-qs-run-to-click-aspnet.png)

    La aplicación continúa la ejecución y se detiene en la línea de código donde se ha hecho clic el botón.

    Comandos de teclado comunes que permiten recorrer el código incluyen **F10** y **F11**. Para obtener instrucciones más detalladas, consulte el [guía para principiantes](../debugger/getting-started-with-the-debugger.md).

## <a name="inspect-variables-in-a-datatip"></a>Inspeccionar las variables en una información sobre datos

1. En la línea actual de código (marcado con el puntero de ejecución amarillo), mantenga el mouse sobre el `c2` objeto con el mouse para mostrar una información sobre datos.

    ![Ver una información sobre datos](../debugger/media/dbg-qs-data-tip-aspnet.png)

    La información sobre datos muestra el valor actual de la `c2` variable y le permite inspeccionar sus propiedades. Al depurar, si ve un valor que no esperaba, probablemente tenga un error en las líneas de código anteriores o que realiza la llamada. 

2. Expanda la información sobre datos para buscar en los valores de propiedad actuales de la `c2` objeto.

3. Si desea anclar la información sobre datos para que pueda continuar ver el valor de `c2` mientras se ejecuta el código, haga clic en el icono de anclaje pequeño. (Puede mover la información sobre datos a una ubicación adecuada).

## <a name="edit-code-and-continue-debugging"></a>Editar código y continuar con la depuración

Si se identifica un cambio que desea probar en el código durante una sesión de depuración, puede hacerlo, demasiado.

1. En el `OnGet` método, haga clic en la segunda instancia de `result.First.Value` y cambiar `result.First.Value` a `result.Last.Value`.

1. Presione **F10** (o **Depurar > paso a paso por**) pocas veces para avanzar el depurador y ejecutar el código revisado.

    ![Editar y continuar](../debugger/media/dbg-qs-edit-and-continue-aspnet.png "editar y continuar")

    **F10** hace avanzar la instrucción de depurador uno en uno, pero pasos sobre las funciones en lugar de ejecución paso a paso en ellos (que omita aún se ejecuta el código).

Para obtener más información sobre el uso de editar y continuar y las limitaciones de características, vea [editar y continuar](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Pasos siguientes

- Para obtener más información sobre el depurador, consulte [para iniciar el depurador y navegar por código](../debugger/getting-started-with-the-debugger.md).
- Para obtener más información acerca de los puntos de interrupción, consulte [usar puntos de interrupción](../debugger/using-breakpoints.md).

## <a name="see-also"></a>Vea también  
 [Depurar en Visual Studio](../debugger/index.md)  
 [Guía de características del depurador](../debugger/debugger-feature-tour.md)
