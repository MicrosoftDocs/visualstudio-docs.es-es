---
title: Depurar una aplicación multiproceso
description: Depurar con la ventana subprocesos y la barra de herramientas ubicación de depuración en Visual Studio
ms.date: 11/21/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- multithreaded debugging, tutorial
- tutorials, multithreaded debugging
ms.assetid: adfbe002-3d7b-42a9-b42a-5ac0903dfc25
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e3a87fd0480727a524b36ab209f5126b0f996c30
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62846928"
---
# <a name="walkthrough-debug-a-multithreaded-app-using-the-threads-window-c-visual-basic-c"></a>Tutorial: Depurar una aplicación multiproceso mediante la ventana de subprocesos (C#, Visual Basic, C++)

Varios elementos de interfaz de usuario de Visual Studio ayudan a depurar aplicaciones multiproceso. Este artículo presentan las características de depuración multiproceso en la ventana del editor de código, **ubicación de depuración** barra de herramientas, y **subprocesos** ventana. Para obtener información acerca de otras herramientas para depurar aplicaciones multiproceso, vea [empezar a depurar aplicaciones multiproceso](../debugger/get-started-debugging-multithreaded-apps.md).

Completar este tutorial dura sólo unos minutos y le ayuda a familiarizarse con los conceptos básicos de depurar aplicaciones multiproceso.

## <a name="create-a-multithreaded-app-project"></a>Crear un proyecto de aplicación multiproceso

Cree el siguiente proyecto de aplicación multiproceso para utilizarla en este tutorial:

1. Abra Visual Studio y cree un nuevo proyecto.

    ::: moniker range=">=vs-2019"
    Presione **Esc** para cerrar la ventana de inicio. Tipo **Ctrl + Q** para abrir el cuadro de búsqueda, escriba **consola** (o **c ++** ), elija **plantillas**y, a continuación:

    - Para C#, elija **crear nuevo proyecto de aplicación de consola (.NET Framework)** para C#. En el cuadro de diálogo que se abre, elija **Crear**.
    - Para C++, elija **crear nuevo proyecto de aplicación de consola**. En el cuadro de diálogo que se abre, elija **Crear**.

    A continuación, escriba un nombre como **MyThreadWalkthroughApp** y haga clic en **crear**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    En la barra de menús superior, seleccione **Archivo** > **Nuevo** > **Proyecto**. En el panel izquierdo de la **nuevo proyecto** cuadro de diálogo, seleccione lo siguiente:
    - Para un C# aplicación, en **Visual C#** , elija **Windows Desktop**y, a continuación, en el panel central, elija **aplicación de consola (.NET Framework)** .
    - Para un C++ aplicación, en **Visual C++** , elija **Windows Desktop**,, y, a continuación, elija **aplicación de consola Windows**.

    A continuación, escriba un nombre como **MyThreadWalkthroughApp** y haga clic en **Aceptar**.
    ::: moniker-end

    Si no ve la plantilla de proyecto **Aplicación de consola**, vaya a **Herramientas** > **Obtener herramientas y características…** y se abrirá el instalador de Visual Studio. Seleccione la carga de trabajo **Desarrollo de escritorio de .NET** o **Desarrollo para el escritorio con C++** y, luego, elija **Modificar**.

    Aparece el nuevo proyecto en **el Explorador de soluciones**, y un archivo de origen denominado *Program.cs* o *MyThreadWalkthroughApp.cpp* se abre en la ventana de código fuente.

1. Reemplace el código en el archivo de origen con la C# o C++ código de ejemplo de [empezar a depurar aplicaciones multiproceso](../debugger/get-started-debugging-multithreaded-apps.md).

1. Seleccione **archivo** > **guardar todo**.

## <a name="start-debugging"></a>Iniciar depuración

1. Busque las líneas siguientes en el código fuente:

   ```csharp
   Thread.Sleep(3000);
   Console.WriteLine();
   ```

   ```C++
   Thread::Sleep(3000);
   Console.WriteLine();
   ```

1. Establecer un punto de interrupción en el `Console.WriteLine();` línea haciendo clic en el medianil izquierdo, o al seleccionar la línea y presionando **F9**.

   El punto de interrupción aparece como un círculo rojo en el medianil izquierdo al lado de la línea de código.

1. Seleccione **depurar** > **Iniciar depuración**, o bien presione **F5**.

   La aplicación se inicia en modo de depuración y se detiene en el punto de interrupción.

1. En el modo de interrupción, abra el **subprocesos** ventana seleccionando **depurar** > **Windows** > **subprocesos**. Debe estar en una sesión de depuración para abrir o ver el **subprocesos** y otras ventanas de depuración.

## <a name="examine-thread-markers"></a>Examine los marcadores de subprocesos

1. En el código fuente, busque el `Console.WriteLine();` línea.

   1. Haga clic en el **subprocesos** ventana y seleccione **Mostrar subprocesos en código fuente** ![Mostrar subprocesos en código fuente](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker") en el menú.

   El medianil junto al código fuente de la línea muestra ahora un *marcador de subproceso* icono ![marcador de subproceso](../debugger/media/dbg-thread-marker.png "marcador de subproceso"). El marcador de subproceso indica que un subproceso se ha detenido en esa ubicación. Si hay más de un subproceso detenido en la ubicación, el ![varios subprocesos](../debugger/media/dbg-multithreaded-show-threads.png "varios subprocesos") aparece el icono.

1. Desplace el puntero sobre el marcador de subproceso. Aparece una información sobre datos, que muestra el número de Id. de nombre y el subproceso para el subproceso detenido o subprocesos. Los nombres de subproceso pueden ser `<No Name>`.

   >[!TIP]
   >Para ayudar a identificar los subprocesos sin nombre, puede cambiar el nombre en el **subprocesos** ventana. Haga clic en el subproceso y seleccione **cambiar el nombre**.

1. Haga clic en el marcador de subproceso en el código fuente para ver las opciones disponibles en el menú contextual.

## <a name="flag-and-unflag-threads"></a>Marcar y desmarcar subprocesos

Puede marcar los subprocesos para realizar un seguimiento de los que desea prestar especial atención a los subprocesos.

Marcar y desmarcar subprocesos desde el editor de código fuente o desde el **subprocesos** ventana. Elija si desea mostrar solo marcados subprocesos o todos los subprocesos, desde el **ubicación de depuración** o **subprocesos** las barras de herramientas de la ventana. Las selecciones realizadas desde cualquier ubicación afecta a todas las ubicaciones.

### <a name="flag-and-unflag-threads-in-source-code"></a>Marcar y desmarcar subprocesos en código fuente

1. Abra el **ubicación de depuración** barra de herramientas seleccionando **vista** > **las barras de herramientas** > **ubicación de depuración**. También puede haga clic en el área de barra de herramientas y seleccione **ubicación de depuración**.

1. El **ubicación de depuración** barra de herramientas tiene tres campos: **Proceso**, **subprocesos**, y **marco de pila**. Lista desplegable el **subprocesos** lista y tenga en cuenta cuántos subprocesos no existe. En el **subproceso** lista, el subproceso actualmente en ejecución se ha marcado por un **>** símbolos.

1. En la ventana de código fuente, mantenga el mouse sobre un icono de marcador de subproceso en el margen interno y seleccione el icono de marca (o uno de los iconos de indicador vacío) en la información sobre datos. El icono de marca cambia a rojo.

   También puede haga clic en un icono de marcador de subproceso, apunte a **marca**y, a continuación, seleccione un subproceso para marcar en el menú contextual.

1. En el **ubicación de depuración** barra de herramientas, seleccione el **mostrar sólo subprocesos marcados** icono ![Mostrar subprocesos marcados](../debugger/media/dbg-threads-show-flagged.png "Mostrar subprocesos marcados"), a la derecho de la **subprocesos** campo. El icono está deshabilitado, a menos que se marcan uno o varios subprocesos.

   Sólo el subproceso marcado aparece ahora en el **subproceso** lista desplegable en la barra de herramientas. Para volver a mostrar todos los subprocesos, seleccione el **mostrar sólo subprocesos marcados** nuevo icono.

   >[!TIP]
   >Después de que algunos subprocesos marcados, puede colocar el cursor en el editor de código, contextual y seleccione **ejecutar subprocesos marcados al Cursor**. Asegúrese de elegir llegará a todos los subprocesos marcan de código. **Ejecutar subprocesos marcados hasta el Cursor** pausará subprocesos en la línea seleccionada del código, lo que facilita controlar el orden de ejecución por [inmovilizar y reanudar subprocesos](#bkmk_freeze).

1. Para alternar el estado marcado o marcado del subproceso actualmente en ejecución, seleccione la única marca **estado de alternancia actual subproceso marcados** botón de barra de herramientas a la izquierda de la **mostrar sólo subprocesos marcados** botón. Marcar el subproceso actual es útil para buscar el subproceso actual cuando se muestran solo subprocesos marcados.

1. Para quitar el marcador de un subproceso, mantenga el mouse sobre el marcador de subproceso en el código fuente y seleccione el icono de indicador rojo para desactivarla, o haga clic en el marcador de subproceso y seleccione **Quitar marcador**.

### <a name="flag-and-unflag-threads-in-the-threads-window"></a>Marcar y desmarcar subprocesos en la ventana subprocesos

En el **subprocesos** ventana, subproceso marcado tiene rojo marca iconos junto a ellos, mientras que los subprocesos sin marcar, si se muestra, tienen iconos vacíos.

![Ventana de subprocesos](../debugger/media/dbg-threads-window.png "ventana de subprocesos")

Seleccione un icono de marca para cambiar el estado del subproceso marcado o marcado, según su estado actual.

También puede haga clic en una línea y seleccione **marca**, **Quitar marcador**, o **desmarcar todos los subprocesos** en el menú contextual.

El **subprocesos** barra de herramientas ventana también tiene un **mostrar solo subprocesos de marcados** botón, que es el derecho de uno de los iconos de indicador de dos. Funciona igual que el botón en el **ubicación de depuración** barra de herramientas y cualquiera de los botones controla la presentación en ambas ubicaciones.

### <a name="other-threads-window-features"></a>Otras características de la ventana subprocesos

En el **subprocesos** ventana, seleccione el encabezado de cualquier columna para ordenar los subprocesos por esa columna. Vuelva a seleccionar para invertir el criterio de ordenación. Si se muestran todos los subprocesos, seleccionando la columna de icono de marca ordena los subprocesos por estado marcado o marcado.

La segunda columna de la **subprocesos** ventana (con ningún encabezado) es el **actual subproceso** columna. Una flecha amarilla en esta columna marca el punto de ejecución actual.

El **ubicación** columna muestra dónde aparece cada subproceso en el código fuente. Seleccione la flecha de expansión situada junto a la **ubicación** entrada, o mantenga el puntero sobre la entrada, para mostrar una pila de llamadas parcial para ese subproceso.

>[!TIP]
>Para obtener una vista gráfica de las pilas de llamadas de subprocesos, use el [pilas paralelas](../debugger/using-the-parallel-stacks-window.md) ventana. Para abrir la ventana, durante la depuración, seleccione **depurar**> **Windows** > **pilas paralelas**.

Además **marca**, **Quitar marcador**, y **desmarcar todos los subprocesos**, el menú contextual para **subprocesos** tiene elementos de la ventana:

- El **Mostrar subprocesos en código fuente** botón.
- **Presentación hexadecimal**, los cambios que el **Id. del subproceso**s en el **subprocesos** ventana de decimal a formato hexadecimal.
- [Cambiar a subproceso](#switch-to-another-thread), que activa inmediatamente la ejecución en ese subproceso.
- **Cambiar el nombre de**, que le permite cambiar el nombre del subproceso.
- [Inmovilizar y descongelar](#bkmk_freeze) comandos.

## <a name="bkmk_freeze"></a> Inmovilizar y reanudar la ejecución de subprocesos

Puede inmovilizar y reanudar, o suspender y reanudar subprocesos para controlar el orden en que los subprocesos realizan el trabajo. Inmovilizar y reanudar subprocesos pueden ayudarle a resolver los problemas de simultaneidad, como interbloqueos y condiciones de carrera.

> [!TIP]
> Para seguir un único subproceso sin inmovilizar otros subprocesos, que también es un escenario de depuración comunes, vea [empezar a depurar aplicaciones multiproceso con comportamiento](../debugger/get-started-debugging-multithreaded-apps.md#bkmk_follow_a_thread).

**Para inmovilizar y descongelar subprocesos:**

1. En el **subprocesos** ventana, haga clic en cualquier subproceso y, a continuación, seleccione **inmovilizar**. Un **pausar** icono en el **actual subproceso** columna indica que el subproceso está inmovilizado.

1. Seleccione **columnas** en el **subprocesos** barra de herramientas ventana y, a continuación, seleccione **número de suspendidos** para mostrar el **número de suspendidos** columna. Es el valor de recuento de suspensión del subproceso inmovilizado **1**.

1. Haga clic en el subproceso inmovilizado y seleccione **reanudar**.

   El **pausar** icono desaparece y el **número de suspendidos** valor cambia a **0**.

## <a name="switch-to-another-thread"></a>Cambiar a otro subproceso

Es posible que vea un **la aplicación está en modo de interrupción** ventana cuando se intenta cambiar a otro subproceso. Esta ventana indica que el subproceso no tiene ningún código que puede mostrar el depurador actual. Por ejemplo, es posible que se puede depurar código administrado, pero el subproceso es código nativo. La ventana ofrece sugerencias para resolver el problema.

**Para cambiar a otro subproceso:**

1. En el **subprocesos** ventana, anote el identificador de subproceso actual, que es el subproceso con una flecha amarilla en el **actual subproceso** columna. Desea volver a este subproceso para continuar con la aplicación.

1. Haga clic en un subproceso diferente y seleccione **cambiar a subproceso** en el menú contextual.

1. Observe que ha cambiado la ubicación de la flecha amarilla en el **subprocesos** ventana. El marcador de subproceso actual original también se conserva como un esquema.

   Examine la información sobre herramientas en el marcador de subproceso en el editor de código fuente y en la lista de los **subproceso** lista desplegable en el **ubicación de depuración** barra de herramientas. Observe que el subproceso actual también ha cambiado ahí.

1. En el **ubicación de depuración** barra de herramientas, seleccione un subproceso diferente de la **subproceso** lista. Observe que el subproceso actual también los cambios en las dos ubicaciones.

1. En el editor de código fuente, haga clic en un marcador de subproceso, apunte a **cambiar a subproceso**y seleccione otro subproceso de la lista. Observe que el subproceso actual cambia en las tres ubicaciones.

Con el marcador de subproceso en código fuente, puede cambiar sólo a los subprocesos que se detienen en esa ubicación. Utilizando la ventana **Subprocesos** y la barra de herramientas **Ubicación de depuración**, puede cambiar a cualquier subproceso.

Ahora que ha aprendido los conceptos básicos de depurar aplicaciones multiproceso. Puede observar, marcar y desmarcar e inmovilizar y reanudar subprocesos mediante el uso de la **subprocesos** ventana, el **subproceso** lista en el **ubicación de depuración** barra de herramientas o los marcadores de subprocesos en el editor de código fuente.

## <a name="see-also"></a>Vea también
- [Depuración de aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Cómo: cambiar a otro subproceso durante la depuración](../debugger/how-to-switch-to-another-thread-while-debugging.md)
