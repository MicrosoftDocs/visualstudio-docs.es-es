---
title: Depuración de ASP.NET Core
description: Depuración de ASP.NET Core con el depurador de Visual Studio
ms.custom: mvc
ms.date: 08/06/2018
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: f4cea2e1-08dc-47ac-aba2-3b8c338e607f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: bbe3d23301f0853626a930855acf4b595c6a2923
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2020
ms.locfileid: "75847874"
---
# <a name="quickstart-debug-aspnet-core-with-the-visual-studio-debugger"></a>Inicio rápido: Depuración de ASP.NET Core con el depurador de Visual Studio

El depurador de Visual Studio proporciona muchas características de gran eficacia para ayudar a depurar aplicaciones. En este tema se proporciona una forma rápida de obtener información sobre las características básicas.

## <a name="create-a-new-project"></a>Crear un proyecto nuevo

1. Abra Visual Studio.

    ::: moniker range=">=vs-2019"
    Presione **Esc** para cerrar la ventana de inicio. Presione **Ctrl + Q** para abrir el cuadro de búsqueda, escriba **asp.net**, elija **Plantillas** y luego, **Crear una aplicación web ASP.NET Core**. En el cuadro de diálogo que se abre, elija **Crear**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    En la barra de menús superior, elija **Archivo** > **Nuevo** > **Proyecto**. En el panel izquierdo del cuadro de diálogo **Nuevo proyecto**, en **Visual C#** , elija **Web** y luego, en el panel central, **Aplicación web ASP.NET Core**. Escriba un nombre como **MyDbgApp** y haga clic en **Aceptar**.

    En el cuadro de diálogo que aparece, elija **Aplicación web** en el panel central y luego haga clic en **Aceptar**.

    ![Elección de una aplicación web](../debugger/media/dbg-qs-aspnet-choose-web-app.png)
    ::: moniker-end

    Si no ve la plantilla de proyecto **Aplicación web ASP.NET**, vaya a **Herramientas** > **Obtener herramientas y características…** y se abrirá el Instalador de Visual Studio. Elija la carga de trabajo **Desarrollo de ASP.NET y web** y después elija **Modificar**.

    Visual Studio crea el proyecto.

1. En el Explorador de soluciones, abra About.cshtml.cs (en Pages/About.cshtml) y reemplace el código siguiente

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

Un *punto de interrupción* es un marcador que indica en qué punto debe Visual Studio suspender la ejecución de código para poder echar un vistazo a los valores de variables, o al comportamiento de memoria, o si se está ejecutando o no una rama de código. Es la característica más básica de la depuración.

1. Para establecer el punto de interrupción, haga clic en el medianil de la izquierda de la función `doWork` (o seleccione la línea de código y presione **F9**).

    ![Establecer un punto de interrupción](../debugger/media/dbg-qs-set-breakpoint-aspnet.png)

    El punto de interrupción se establece a la izquierda de la llave de apertura (`{`).

1. Ahora presione **F5** (o elija **Depurar > Iniciar depuración**).

1. Cuando se cargue la página web, haga clic en el vínculo **Acerca de** de la parte superior de la página web.

    El depurador se detiene donde se ha establecido el punto de interrupción. La instrucción donde se ha detenido la ejecución del depurador y la aplicación se indica mediante la flecha amarilla. La línea con la llave de apertura (`{`) después de la declaración de función `doWork` aún no se ha ejecutado.

    ![Llegar a un punto de interrupción](../debugger/media/dbg-qs-hit-breakpoint-aspnet.png)

    > [!TIP]
    > Si tiene un punto de interrupción en un bucle o recursión, o si tiene muchos puntos de interrupción que ejecuta paso a paso con frecuencia, use un [punto de interrupción condicional](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) para asegurarse de que el código se suspende ÚNICAMENTE cuando se cumplen determinadas condiciones. Esto ahorra tiempo y además puede facilitar la depuración de problemas que son difíciles de reproducir.

## <a name="navigate-code"></a>Navegación en el código

Hay distintos comandos para indicar al depurador que continúe. Aquí se muestra un comando de navegación de código muy útil disponible a partir de Visual Studio 2017.

Mientras la ejecución está detenida en el punto de interrupción, mantenga el puntero sobre la instrucción `return c2` hasta que aparezca el botón verde **Run to click** (Ejecutar hasta clic) ![Ejecutar hasta clic](../debugger/media/dbg-tour-run-to-click.png) y luego presione el botón **Ejecutar hasta clic**.

![Ejecutar hasta clic](../debugger/media/dbg-qs-run-to-click-aspnet.png)

La aplicación se sigue ejecutando y se detiene en la línea de código donde se ha hecho clic en el botón.

Los comandos de teclado habituales usados para ejecutar el código paso a paso son **F10** y **F11**. Para obtener instrucciones más detalladas, vea [Primer vistazo al depurador](../debugger/debugger-feature-tour.md).

## <a name="inspect-variables-in-a-datatip"></a>Inspeccionar las variables de una información sobre datos

1. En la línea de código actual (marcada con el puntero de ejecución amarillo), mantenga el puntero sobre el objeto `c2` para mostrar una información sobre datos.

    ![Visualización de información sobre datos](../debugger/media/dbg-qs-data-tip-aspnet.png)

    La información sobre datos muestra el valor actual de la variable `c2` y permite inspeccionar sus propiedades. Al depurar, si ve un valor que no esperaba, probablemente tenga un error en las líneas de código anteriores o de llamada.

2. Expanda la información sobre datos para ver los valores de propiedad actuales del objeto `c2`.

3. Si quiere anclar la información sobre datos para poder seguir viendo el valor de `c2` mientras ejecuta el código, haga clic en el icono de anclar pequeño. (Puede mover la información sobre datos anclada a una ubicación que le resulte cómoda).

## <a name="edit-code-and-continue-debugging"></a>Editar código y seguir depurando

Si identifica un cambio que quiere probar en el código a mitad de una sesión de depuración, también puede hacerlo.

1. En el método `OnGet`, haga clic en la segunda instancia de `result.First.Value` y cambie `result.First.Value` por `result.Last.Value`.

1. Presione **F10** (o **Depurar > Saltar**) varias veces para que el depurador avance y ejecute el código editado.

    ![Editar y continuar](../debugger/media/dbg-qs-edit-and-continue-aspnet.png "Editar y continuar")

    **F10** hace que el depurador avance de instrucción en instrucción, pero que se salte las funciones en lugar de depurarlas (el código que se omite se sigue ejecutando).

Para obtener más información sobre el uso de Editar y continuar y las limitaciones de las características, vea [Editar y continuar](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Pasos siguientes

En este tutorial, ha aprendido a iniciar el depurador, a ejecutar el código paso a paso y a inspeccionar variables. Puede ser que le interese analizar las características del depurador con más detenimiento, así como consultar los vínculos disponibles con más información.

> [!div class="nextstepaction"]
> [Primer vistazo al depurador](../debugger/debugger-feature-tour.md)
