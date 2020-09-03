---
title: Depuración de una aplicación multiproceso
description: Depuración mediante la ventana Subprocesos y la barra de herramientas Ubicación de depuración de Visual Studio
ms.date: 02/14/2020
ms.topic: how-to
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
ms.openlocfilehash: 33375a8970638765d02a94e6e3e9cd8afc1a0fe7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85348657"
---
# <a name="walkthrough-debug-a-multithreaded-app-using-the-threads-window-c-visual-basic-c"></a>Tutorial: Depuración de una aplicación multiproceso mediante la ventana Subprocesos (C#, Visual Basic, C++)

Existen varios elementos de la interfaz de usuario de Visual Studio que le ayudan a depurar aplicaciones multiproceso. En este artículo se presentan las características de depuración multiproceso de la ventana del editor de código, la barra de herramientas **Ubicación de depuración** y la ventana **Subprocesos**. Para obtener información sobre otras herramientas para depurar aplicaciones multiproceso, consulte [Introducción a la depuración de aplicaciones multiproceso](../debugger/get-started-debugging-multithreaded-apps.md).

Completar este tutorial solo le llevará unos minutos y le ayudará a familiarizarse con los aspectos básicos de la depuración de aplicaciones multiproceso.

## <a name="create-a-multithreaded-app-project"></a>Creación de un proyecto de aplicación multiproceso

Cree el siguiente proyecto de aplicación multiproceso para usarlo en este tutorial:

1. Abra Visual Studio y cree un nuevo proyecto.

   ::: moniker range=">=vs-2019"

   Si la ventana de inicio no está abierta, elija **Archivo** > **Ventana Inicio**.

   En la ventana de inicio, elija **Crear un proyecto nuevo**.

   En el cuadro de búsqueda de la ventana **Crear un proyecto**, escriba *consola*. A continuación, elija **C#** o **C++** en la lista de lenguajes y, luego, **Windows** en la lista de plataformas. 

   Después de aplicar los filtros de lenguaje y plataforma, elija la plantilla **Aplicación de consola (.NET Core)** o, para C++, la plantilla **Aplicación de consola** y, después, elija **Siguiente**.

   > [!NOTE]
   > Si no ve la plantilla correcta, vaya a **Herramientas** > **Obtener herramientas y características...** para abrir el Instalador de Visual Studio. Seleccione la carga de trabajo **Desarrollo de escritorio de .NET** o **Desarrollo para el escritorio con C++** y, luego, elija **Modificar**.

   En la ventana **Configurar el nuevo proyecto**, escriba *MyThreadWalkthroughApp* en el cuadro **Nombre del proyecto**. Luego, elija **Crear**.

   ::: moniker-end
   ::: moniker range="vs-2017"
   En la barra de menús superior, elija **Archivo** > **Nuevo** > **Proyecto**. En el panel izquierdo del cuadro de diálogo **Nuevo proyecto**, elija lo siguiente:

   - Para una aplicación de C#, en **Visual C#** , elija **Escritorio de Windows** y, después, en el panel central, **Aplicación de consola (.NET Framework)** .
   - Para una aplicación de C++, en **Visual C++** , elija **Escritorio de Windows** y después, **Aplicación de consola Windows**.

   Si no ve la plantilla de proyecto **Aplicación de consola (.NET Core)** o, para C++, **Aplicación de consola**, vaya a **Herramientas** > **Obtener herramientas y características…** para abrir el Instalador de Visual Studio. Seleccione la carga de trabajo **Desarrollo de escritorio de .NET** o **Desarrollo para el escritorio con C++** y, luego, elija **Modificar**.

   Luego escriba un nombre como *MyThreadWalkthroughApp* y haga clic en **Aceptar**.

   Seleccione **Aceptar**.
   ::: moniker-end

   Aparecerá un nuevo proyecto de consola. Una vez que se ha creado el proyecto, aparece un archivo de código fuente. En función del lenguaje elegido, el archivo de código fuente se podría denominar *Program.cs*, *MyThreadWalkthroughApp.cpp* o *Module1.vb*.

1. Reemplace el código del archivo de código fuente por el código de ejemplo de C# o C++ que encontrará en [Introducción a la depuración de aplicaciones multiproceso](../debugger/get-started-debugging-multithreaded-apps.md).

1. Seleccione **Archivo** > **Guardar todo**.

## <a name="start-debugging"></a>Iniciar depuración

1. Busque las siguientes líneas en el código fuente:

   ```csharp
   Thread.Sleep(3000);
   Console.WriteLine();
   ```

   ```C++
   Thread::Sleep(3000);
   Console.WriteLine();
   ```

1. Establezca un punto de interrupción en la línea `Console.WriteLine();`; para ello, haga clic en el medianil izquierdo o seleccione la línea y presione **F9**.

   El punto de interrupción aparece como un círculo rojo en el medianil izquierdo junto a la línea de código.

1. Seleccione **Depurar** > **Iniciar depuración** o bien presione **F5**.

   La aplicación se inicia en modo de depuración y se pausa en el punto de interrupción.

1. En el modo de interrupción, abra la ventana **Subprocesos**; para ello, seleccione **Depurar** > **Windows**  > **Subprocesos**. Para poder abrir o ver la ventana **Subprocesos** y las demás ventanas de depuración, debe estar en una sesión de depuración.

## <a name="examine-thread-markers"></a>Examen de los marcadores de subproceso

1. En el código fuente, busque la línea `Console.WriteLine();`.

   1. Haga clic con el botón derecho en la ventana **Subprocesos** y seleccione **Mostrar subprocesos en origen** ![Mostrar subprocesos en origen](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker") en el menú.

   El medianil junto a la línea de código fuente ahora muestra un icono de *marcador de subproceso* ![Marcador de subproceso](../debugger/media/dbg-thread-marker.png "Marcador de subproceso"). El marcador de subproceso indica que un subproceso se ha detenido en esa ubicación. Si hay más de un subproceso detenido en la ubicación, aparece el icono de ![varios subprocesos](../debugger/media/dbg-multithreaded-show-threads.png "varios subprocesos").

1. Desplace el puntero sobre el marcador de subproceso. Aparece una sugerencia de datos en la que se muestra el nombre y el id. de subproceso del subproceso o subprocesos detenidos. Los nombres de los subprocesos pueden ser `<No Name>`.

   >[!TIP]
   >Para facilitar la identificación de los subprocesos sin nombre, puede cambiar su nombre en la ventana **Subprocesos**. Haga clic con el botón derecho en el subproceso y seleccione **Cambiar nombre**.

1. Haga clic con el botón derecho en el marcador de subproceso del código fuente para ver las opciones disponibles en el menú contextual.

## <a name="flag-and-unflag-threads"></a>Marcar y desmarcar subprocesos

Puede marcar los subprocesos para realizar un seguimiento de los subprocesos a los que quiere prestar una atención especial.

Puede marcar y desmarcar los subprocesos desde el editor de código fuente o la ventana **Subprocesos**. En las barras de herramientas de las ventanas **Ubicación de depuración** o **Subprocesos**, elija si quiere mostrar solo los subprocesos marcados o todos los subprocesos. Las selecciones que realice desde cualquier ubicación afectan a todas las ubicaciones.

### <a name="flag-and-unflag-threads-in-source-code"></a>Marcado y desmarcado de subprocesos en código fuente

1. Abra la barra de herramientas **Ubicación de depuración**; para ello, seleccione **Ver** > **Barras de herramientas** > **Ubicación de depuración**. También puede hacer clic con el botón derecho en el área de la barra de herramientas y seleccionar **Ubicación de depuración**.

1. La barra de herramientas **Ubicación de depuración** tiene tres campos: **Proceso**, **Subproceso** y **Marco de pila**. Despliegue la lista **Subproceso** para observar cuántos subprocesos hay. En la lista **Subprocesos**, el subproceso que se está ejecutando se marca con un símbolo **>** .

1. En la ventana de código fuente, mantenga el puntero sobre un icono de marcador de subproceso del medianil y seleccione el icono de marcado (o uno de los iconos de marcado vacíos) de la sugerencia de datos. El icono de marcado se vuelve rojo.

   También puede hacer clic con el botón derecho en un icono de marcador de subproceso, apuntar a **Marcar** y, a continuación, seleccionar un subproceso para marcarlo en el menú contextual.

1. En la barra de herramientas **Ubicación de depuración**, seleccione el icono **Mostrar solo subprocesos marcados** ![Mostrar subprocesos marcados](../debugger/media/dbg-threads-show-flagged.png "Mostrar subprocesos marcados"), ubicado a la derecha del campo **Subproceso**. El icono aparecerá atenuado a menos que se hayan marcado uno o más subprocesos.

   Ahora solo se muestra el subproceso marcado en la lista desplegable **Subproceso** de la barra de herramientas. Para que se vuelvan a mostrar todos los subprocesos, seleccione de nuevo el icono **Mostrar solo subprocesos marcados**.

   >[!TIP]
   >Después de haber marcado algunos subprocesos, puede colocar el cursor en el editor de código, hacer clic con el botón derecho y seleccionar **Ejecutar subprocesos marcados hasta el cursor**. Asegúrese de elegir código al que accedan todos los subprocesos marcados. **Ejecutar subprocesos marcados hasta el cursor** pausará los subprocesos en la línea de código seleccionada, lo que facilita el control del orden de ejecución mediante la [inmovilización y reanudación de los subprocesos](#bkmk_freeze).

1. Para alternar el estado de marcado o desmarcado del subproceso que se está ejecutando actualmente, seleccione el botón de la barra de herramientas de marca única **Alternar estado de marcado del subproceso actual**, situado a la izquierda del botón **Mostrar solo subprocesos marcados**. Marcar el subproceso actual es útil para encontrar el subproceso actual cuando solo se muestran los subprocesos marcados.

1. Para quitar la marca de un subproceso, mantenga el puntero sobre el marcador de subproceso en el código fuente y seleccione el icono de marca roja para borrarlo, o bien haga clic con el botón derecho en el marcador de subproceso y seleccione **Desmarcar**.

### <a name="flag-and-unflag-threads-in-the-threads-window"></a>Marcado y desmarcado de subprocesos en la ventana Subprocesos

En la ventana **Subprocesos**, los subprocesos marcados tienen iconos de marca roja junto a ellos, mientras que los subprocesos no marcados, si se muestran, tienen iconos vacíos.

![Ventana Subprocesos](../debugger/media/dbg-threads-window.png "Ventana de subprocesos")

Seleccione un icono de marca para cambiar el estado del subproceso a marcado o desmarcado, en función de su estado actual.

También puede hacer clic con el botón derecho en una línea y seleccionar **Marcar**, **Desmarcar** o **Desmarcar todos los subprocesos** en el menú contextual.

La barra de herramientas de la ventana **Subprocesos** también tiene un botón **Mostrar solo subprocesos marcados**, situado a la derecha de los dos iconos de marcado. Funciona igual que el botón de la barra de herramientas **Ubicación de depuración**, y ambos botones controlan la presentación en ambas ubicaciones.

### <a name="other-threads-window-features"></a>Otras características de la ventana Subprocesos

En la ventana **Subprocesos**, seleccione el encabezado de cualquier columna para ordenar los subprocesos por esa columna. Seleccione de nuevo para invertir el criterio de ordenación. Si se muestran todos los subprocesos, al seleccionar la columna del icono de marcado, los subprocesos se ordenan por el estado de marcado o no marcado.

La segunda columna de la ventana **Subprocesos** (sin encabezado) es la columna **Subproceso actual**. Una flecha amarilla en esta columna indica el punto de ejecución actual.

La columna **Ubicación** muestra el lugar donde aparece cada subproceso en el código fuente. Seleccione la flecha de expansión situada junto a la entrada **Ubicación**, o bien mantenga el puntero sobre la entrada para mostrar una pila de llamadas de línea de código parcialmente ejecutada para ese subproceso.

>[!TIP]
>Para ver una vista gráfica de las pilas de llamadas de los subprocesos, utilice la ventana [Pilas paralelas](../debugger/using-the-parallel-stacks-window.md). Para abrir la ventana, durante la depuración, seleccione **Depurar**> **Ventanas** > **Pilas paralelas**.

Además de **Marcar**, **Desmarcar** y **Desmarcar todos los subprocesos**, el menú contextual de la ventana **Subprocesos** contiene los elementos siguientes:

- El botón **Mostrar subprocesos en origen**.
- **Visualización hexadecimal**, que cambia los **id. de subproceso** de la ventana **Subprocesos** del formato decimal al formato hexadecimal.
- [Cambiar a subproceso](#switch-to-another-thread), que cambia inmediatamente la ejecución a ese subproceso.
- **Cambiar nombre**, que le permite cambiar el nombre del subproceso.
- Los comandos [Inmovilizar y reanudar](#bkmk_freeze).

## <a name="freeze-and-thaw-thread-execution"></a><a name="bkmk_freeze"></a> Inmovilización y reanudación de la ejecución de subprocesos

Puede inmovilizar y reanudar (suspender y continuar) los subprocesos para controlar el orden en el que realizan el trabajo. Inmovilizar y reanudar los subprocesos puede ayudarle a resolver incidencias de simultaneidad, como, por ejemplo, interbloqueos y condiciones de carrera.

> [!TIP]
> Para seguir un único subproceso sin inmovilizar otros subprocesos, que es también un escenario de depuración habitual, consulte [Introducción a la depuración de aplicaciones multiproceso](../debugger/get-started-debugging-multithreaded-apps.md#bkmk_follow_a_thread).

**Para inmovilizar y descongelar subprocesos:**

1. En la ventana **Subprocesos**, haga clic con el botón derecho en cualquier subproceso y, a continuación, seleccione **Inmovilizar**. El icono de **Pausa** de la columna **Subproceso actual** indica que el subproceso está inmovilizado.

1. Seleccione **Columnas** en la barra de herramientas de la ventana **Subprocesos** y, a continuación, **Recuento de suspensión** para mostrar la columna **Recuento de suspensión**. El valor de recuento de suspensión del subproceso inmovilizado es **1**.

1. Haga clic con el botón derecho en el subproceso inmovilizado y seleccione **Reanudar**.

   El icono **Pausa** desaparece y el valor del **Recuento de suspensión** cambia a **0**.

## <a name="switch-to-another-thread"></a>Cambio a otro subproceso

Es posible que vea una ventana **La aplicación está en modo de interrupción** cuando intente cambiar a otro subproceso. Esta ventana le indica que el subproceso no tiene ningún código que el depurador actual pueda mostrar. Por ejemplo, puede que esté depurando código administrado, pero que el subproceso sea código nativo. La ventana ofrece sugerencias para resolver la incidencia.

**Para cambiar a otro subproceso:**

1. En la ventana **Subprocesos**, anote el id. del subproceso actual, que es el subproceso que tiene una flecha amarilla en la columna **Subproceso actual**. Querrá volver a este subproceso para continuar la aplicación.

1. Haga clic con el botón derecho en otro subproceso y seleccione **Cambiar a subproceso** en el menú contextual.

1. Observe que la ubicación de la flecha amarilla ha cambiado en la ventana **Subprocesos**. El marcador de subproceso actual original también permanece como esquema.

   Observe la información sobre herramientas del marcador de subproceso en el editor de código fuente y la lista del menú desplegable **Subproceso** de la barra de herramientas **Ubicación de depuración**. Observe que el subproceso actual también ha cambiado ahí.

1. En la barra de herramientas **Ubicación de depuración**, seleccione otro subproceso de la lista **Subproceso**. Tenga en cuenta que el subproceso actual cambia también en las otras dos ubicaciones.

1. En el editor de código fuente, haga clic con el botón derecho en un marcador de subproceso, apunte a **Cambiar a subproceso** y seleccione otro subproceso de la lista. Observe que el subproceso actual cambia en las tres ubicaciones.

Con el marcador de subproceso en código fuente, solo puede cambiar a subprocesos que se detienen en esa ubicación. Utilizando la ventana **Subprocesos** y la barra de herramientas **Ubicación de depuración**, puede cambiar a cualquier subproceso.

Ahora ha aprendido los aspectos básicos de la depuración de aplicaciones multiproceso. Puede observar, marcar y desmarcar, así como inmovilizar y reanudar subprocesos mediante la ventana **Subprocesos**, la lista **Subproceso** de la barra de herramientas **Ubicación de depuración** o bien los marcadores de subproceso del editor de código fuente.

## <a name="see-also"></a>Vea también
- [Depuración de aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Cómo: cambiar a otro subproceso durante la depuración](../debugger/how-to-switch-to-another-thread-while-debugging.md)
