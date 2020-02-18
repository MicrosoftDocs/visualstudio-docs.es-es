---
title: Depuración de una aplicación multiproceso
description: Depurar mediante la ventana subprocesos y la barra de herramientas ubicación de depuración en Visual Studio
ms.date: 02/14/2020
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
ms.openlocfilehash: eb7b7850d8d7582110152d248683f89981933215
ms.sourcegitcommit: 6ef52c2030b37ea7a64fddb32f050ecfb77dd918
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/17/2020
ms.locfileid: "77416378"
---
# <a name="walkthrough-debug-a-multithreaded-app-using-the-threads-window-c-visual-basic-c"></a>Tutorial: depurar una aplicación multiproceso mediante la ventana subprocesosC#( C++, Visual Basic,)

Varios elementos de la interfaz de usuario de Visual Studio ayudan a depurar aplicaciones multiproceso. En este artículo se presentan las características de depuración multiproceso en la ventana del editor de código, la barra de herramientas **Ubicación de depuración** y la ventana **subprocesos** . Para obtener información sobre otras herramientas para depurar aplicaciones multiproceso, vea Introducción a la [depuración de aplicaciones multiproceso](../debugger/get-started-debugging-multithreaded-apps.md).

Completar este tutorial solo tarda unos minutos y le ayuda a familiarizarse con los aspectos básicos de la depuración de aplicaciones multiproceso.

## <a name="create-a-multithreaded-app-project"></a>Crear un proyecto de aplicación multiproceso

Cree el siguiente proyecto de aplicación multiproceso para usarlo en este tutorial:

1. Abra Visual Studio y cree un nuevo proyecto.

   ::: moniker range=">=vs-2019"

   Si la ventana de inicio no está abierta, elija **Archivo** > **Ventana Inicio**.

   En la ventana de inicio, elija **Crear un proyecto nuevo**.

   En el cuadro de búsqueda de la ventana **Crear un proyecto**, escriba *consola*. A continuación, **C#** elija **C++** o en la lista de idiomas y, a continuación, seleccione **Windows** en la lista de plataformas. 

   Después de aplicar los filtros de idioma y plataforma, elija la **aplicación de consola (.net Core)** o C++, para, plantilla de **aplicación de consola** y, a continuación, elija **siguiente**.

   > [!NOTE]
   > Si no ve la plantilla correcta, vaya a **herramientas** > **obtener herramientas y características...** , que abre el instalador de Visual Studio. Seleccione la carga de trabajo **Desarrollo de escritorio de .NET** o **Desarrollo para el escritorio con C++** y, luego, elija **Modificar**.

   En la ventana **configurar el nuevo proyecto** , escriba o escriba *MyThreadWalkthroughApp* en el cuadro **nombre del proyecto** . Luego, elija **Crear**.

   ::: moniker-end
   ::: moniker range="vs-2017"
   En la barra de menús superior, seleccione **Archivo** > **Nuevo** > **Proyecto**. En el panel izquierdo del cuadro de diálogo **nuevo proyecto** , elija lo siguiente:

   - En el C# caso de una aplicación, en **C#visual**, elija **escritorio de Windows**y, a continuación, en el panel central, elija aplicación de **consola (.NET Framework)** .
   - En el C++ caso de una aplicación, en **C++visual**, elija **escritorio de Windows**y, a continuación, elija aplicación de consola de **Windows**.

   Si no ve la **aplicación de consola (.net Core)** o, para C++, la plantilla de proyecto de **aplicación de consola** , vaya a **herramientas** > **obtener herramientas y características...** , que abre el instalador de Visual Studio. Seleccione la carga de trabajo **Desarrollo de escritorio de .NET** o **Desarrollo para el escritorio con C++** y, luego, elija **Modificar**.

   A continuación, escriba un nombre como *MyThreadWalkthroughApp* y haga clic en **Aceptar**.

   Seleccione **Aceptar**.
   ::: moniker-end

   Aparecerá un nuevo proyecto de consola. Una vez creado el proyecto, aparece un archivo de código fuente. Dependiendo del lenguaje que haya elegido, el archivo de código fuente podría llamarse *Program.CS*, *MyThreadWalkthroughApp. cpp*o *Module1. VB*.

1. Reemplace el código del archivo de código fuente por C# el C++ código de ejemplo o de introducción a la [depuración de aplicaciones multiproceso](../debugger/get-started-debugging-multithreaded-apps.md).

1. Seleccione **Archivo** > **Guardar todo**.

## <a name="start-debugging"></a>Iniciar la depuración

1. Busque las líneas siguientes en el código fuente:

   ```csharp
   Thread.Sleep(3000);
   Console.WriteLine();
   ```

   ```C++
   Thread::Sleep(3000);
   Console.WriteLine();
   ```

1. Establezca un punto de interrupción en la línea de `Console.WriteLine();`; para ello, haga clic en el margen interno izquierdo o seleccione la línea y presione **F9**.

   El punto de interrupción aparece como un círculo rojo en el margen interno izquierdo junto a la línea de código.

1. Seleccione **Depurar** > **iniciar depuración**o presione **F5**.

   La aplicación se inicia en modo de depuración y se pausa en el punto de interrupción.

1. En el modo de interrupción, abra la ventana **subprocesos** seleccionando **depurar** > los **subprocesos**de **Windows** > . Debe estar en una sesión de depuración para abrir o ver los **subprocesos** y otras ventanas de depuración.

## <a name="examine-thread-markers"></a>Examinar marcadores de subprocesos

1. En el código fuente, busque la línea de `Console.WriteLine();`.

   1. Haga clic con el botón secundario en la ventana **subprocesos** y seleccione **Mostrar subprocesos en origen** ![Mostrar subprocesos en origen en](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker") el menú.

   El medianil situado junto a la línea de código fuente ahora muestra un ![marcador](../debugger/media/dbg-thread-marker.png "Marcador de subproceso")de subproceso de icono de *marcador* de subproceso. El marcador de subproceso indica que un subproceso se ha detenido en esa ubicación. Si hay más de un subproceso detenido en la ubicación, aparece el icono de ![varios subprocesos](../debugger/media/dbg-multithreaded-show-threads.png "subprocesos múltiples") .

1. Desplace el puntero sobre el marcador de subproceso. Aparece una información sobre información, que muestra el nombre y el número de identificación del subproceso para los subprocesos detenidos. Los nombres de subprocesos se pueden `<No Name>`.

   >[!TIP]
   >Para ayudar a identificar los subprocesos sin nombre, puede cambiarles el nombre en la ventana **subprocesos** . Haga clic con el botón secundario en el subproceso y seleccione **cambiar nombre**.

1. Haga clic con el botón secundario en el marcador de subproceso del código fuente para ver las opciones disponibles en el menú contextual.

## <a name="flag-and-unflag-threads"></a>Marcar y desmarcar subprocesos

Puede marcar los subprocesos para realizar un seguimiento de los subprocesos a los que desea prestar atención especial.

Marque y desmarque los subprocesos del editor de código fuente o de la ventana **subprocesos** . Elija si desea mostrar solo los subprocesos marcados o todos los subprocesos de las barras de herramientas de la ventana **Ubicación de depuración** o **subprocesos** . Las selecciones realizadas desde cualquier ubicación afectan a todas las ubicaciones.

### <a name="flag-and-unflag-threads-in-source-code"></a>Marcar y desmarcar subprocesos en código fuente

1. Abra la barra de herramientas **Ubicación de depuración** seleccionando **Ver** > **barras de herramientas** > **Ubicación de depuración**. También puede hacer clic con el botón secundario en el área de la barra de herramientas y seleccionar **Ubicación de depuración**.

1. La barra de herramientas **Ubicación de depuración** tiene tres campos: **proceso**, **subproceso**y **marco de pila**. Desplegable la lista de **subprocesos** y observe cuántos subprocesos hay. En la lista de **subprocesos** , el subproceso que se está ejecutando actualmente está marcado por un símbolo de **>** .

1. En la ventana de código fuente, mantenga el mouse sobre un icono de marcador de subproceso en el medianil y seleccione el icono de marca (o uno de los iconos de marca vacío) en la información sobre información. El icono de marca se vuelve rojo.

   También puede hacer clic con el botón secundario en un icono de marcador de subproceso, apuntar a la **marca**y, a continuación, seleccionar un subproceso para marcarlo en el menú contextual.

1. En la barra de herramientas **Ubicación de depuración** , seleccione el icono **Mostrar solo subprocesos marcados** Mostrar subprocesos ![marcados](../debugger/media/dbg-threads-show-flagged.png "Mostrar subprocesos marcados"), a la derecha del campo **subproceso** . El icono aparece atenuado a menos que se marquen uno o más subprocesos.

   Solo el subproceso marcado aparece ahora en la lista desplegable **subproceso** de la barra de herramientas. Para volver a mostrar todos los subprocesos, seleccione el icono **Mostrar solo subprocesos marcados** de nuevo.

   >[!TIP]
   >Después de haber marcado algunos subprocesos, puede colocar el cursor en el editor de código, hacer clic con el botón derecho y seleccionar **Ejecutar subprocesos marcados hasta el cursor**. Asegúrese de elegir el código al que se encontrarán todos los subprocesos marcados. **Ejecutar subprocesos marcados en el cursor** pausará los subprocesos en la línea de código seleccionada, lo que facilita el control del orden de ejecución al [inmovilizar y reanudar los subprocesos](#bkmk_freeze).

1. Para alternar el estado marcado o sin marcar del subproceso que se está ejecutando actualmente, seleccione el botón de la barra de herramientas alternar de marca de **subproceso actual** , situado a la izquierda del botón **Mostrar solo subprocesos marcados** . Marcar el subproceso actual es útil para buscar el subproceso actual cuando solo se muestran los subprocesos marcados.

1. Para quitar la marca de un subproceso, mantenga el mouse sobre el marcador de subproceso en el código fuente y seleccione el icono de marca roja para borrarlo, o haga clic con el botón derecho en el marcador de subproceso y seleccione **desmarcar**.

### <a name="flag-and-unflag-threads-in-the-threads-window"></a>Marcar y desmarcar subprocesos en la ventana subprocesos

En la ventana **subprocesos** , los subprocesos marcados tienen iconos de marca roja junto a ellos, mientras que los subprocesos no marcados, si se muestran, tienen iconos vacíos.

![Ventana Subprocesos](../debugger/media/dbg-threads-window.png "Ventana de subprocesos")

Seleccione un icono de marca para cambiar el estado del subproceso a marcado o sin marcar, en función de su estado actual.

También puede hacer clic con el botón secundario en una línea y seleccionar **marcar, quitar**la **marca**o quitar la **marca de todos los subprocesos** en el menú contextual.

La barra de herramientas de la ventana **subprocesos** también tiene un botón **Mostrar solo subprocesos marcados** , que es el derecho de uno de los dos iconos de marca. Funciona igual que el botón de la barra de herramientas de **Ubicación de depuración** y cualquiera de los botones controla la presentación en ambas ubicaciones.

### <a name="other-threads-window-features"></a>Otras características de la ventana subprocesos

En la ventana **subprocesos** , seleccione el encabezado de cualquier columna para ordenar los subprocesos por esa columna. Seleccione de nuevo para invertir el criterio de ordenación. Si se muestran todos los subprocesos, la selección de la columna icono de marca ordena los subprocesos por estado marcado o no marcado.

La segunda columna de la ventana **subprocesos** (sin encabezado) es la columna de **subproceso actual** . Una flecha amarilla en esta columna marca el punto de ejecución actual.

La columna **Ubicación** muestra dónde aparece cada subproceso en el código fuente. Seleccione la flecha de expansión situada junto a la entrada de **Ubicación** o mantenga el mouse sobre la entrada para mostrar una pila de llamadas parcial para ese subproceso.

>[!TIP]
>Para ver una vista gráfica de las pilas de llamadas de los subprocesos, utilice la ventana [pilas paralelas](../debugger/using-the-parallel-stacks-window.md) . Para abrir la ventana durante la depuración, seleccione **Depurar**> **Windows** > **pilas paralelas**.

Además de **marcar** **, quitar la marca y**quitar la **marca de todos los subprocesos**, el menú contextual de los elementos de la ventana de **subprocesos** tiene:

- Botón **Mostrar subprocesos en origen** .
- **Presentación hexadecimal**, que cambia el **ID. de subproceso**en la ventana **subprocesos** del formato decimal a hexadecimal.
- [Cambiar a subproceso](#switch-to-another-thread), que cambia inmediatamente la ejecución a ese subproceso.
- **Rename**, que permite cambiar el nombre del subproceso.
- [Inmovilizar y reanudar](#bkmk_freeze) comandos.

## <a name="bkmk_freeze"></a>Inmovilizar y reanudar la ejecución de subprocesos

Puede inmovilizar y reanudar, o suspender y reanudar, los subprocesos para controlar el orden en el que los subprocesos realizan el trabajo. Inmovilizar y reanudar subprocesos puede ayudarle a resolver problemas de simultaneidad, como interbloqueos y condiciones de carrera.

> [!TIP]
> Para seguir un solo subproceso sin inmovilizar otros subprocesos, que es también un escenario de depuración común, vea Introducción a la [depuración de aplicaciones multiproceso](../debugger/get-started-debugging-multithreaded-apps.md#bkmk_follow_a_thread).

**Para inmovilizar y descongelar subprocesos:**

1. En la ventana **subprocesos** , haga clic con el botón secundario en cualquier subproceso y seleccione **inmovilizar**. Un icono de **pausa** en la columna **subproceso actual** indica que el subproceso está inmovilizado.

1. Seleccione **columnas** en la barra de herramientas de la ventana **subprocesos** y, a continuación, seleccione **recuento de suspensión** para mostrar la columna **recuento de suspensión** . El valor de recuento de suspensión del subproceso inmovilizado es **1**.

1. Haga clic con el botón derecho en el subproceso inmovilizado y seleccione **reanudar**.

   El icono de **pausa** desaparece y el valor de **recuento suspendido** cambia a **0**.

## <a name="switch-to-another-thread"></a>Cambiar a otro subproceso

Puede ver que **la aplicación está en la ventana modo de interrupción** cuando intenta cambiar a otro subproceso. Esta ventana le indica que el subproceso no tiene ningún código que pueda mostrar el depurador actual. Por ejemplo, puede que esté depurando código administrado, pero el subproceso es código nativo. La ventana de ofrece sugerencias para resolver el problema.

**Para cambiar a otro subproceso:**

1. En la ventana **subprocesos** , tome nota del identificador de subproceso actual, que es el subproceso con una flecha amarilla en la columna de **subproceso actual** . Querrá volver a este subproceso para continuar con la aplicación.

1. Haga clic con el botón secundario en otro subproceso y seleccione **cambiar a subproceso** en el menú contextual.

1. Observe que la ubicación de la flecha amarilla ha cambiado en la ventana **subprocesos** . El marcador de subproceso actual original también permanece como un esquema.

   Observe la información sobre herramientas en el marcador de subproceso en el editor de código fuente y la lista en la lista desplegable **subproceso** de la barra de herramientas **Ubicación de depuración** . Observe que el subproceso actual también ha cambiado ahí.

1. En la barra de herramientas **Ubicación de depuración** , seleccione otro subproceso de la lista **subproceso** . Tenga en cuenta que el subproceso actual cambia también en las otras dos ubicaciones.

1. En el editor de código fuente, haga clic con el botón secundario en un marcador de subproceso, seleccione **cambiar a subproceso**y seleccione otro subproceso de la lista. Observe que el subproceso actual cambia en las tres ubicaciones.

Con el marcador de subproceso en el código fuente, solo puede cambiar a los subprocesos que se detienen en esa ubicación. Utilizando la ventana **Subprocesos** y la barra de herramientas **Ubicación de depuración**, puede cambiar a cualquier subproceso.

Ahora ha aprendido los aspectos básicos de la depuración de aplicaciones multiproceso. Puede observar, marcar y quitar la marca, e inmovilizar y reanudar subprocesos mediante **la ventana subprocesos** , la lista de **subprocesos** de la barra de herramientas **Ubicación de depuración** o los marcadores de subproceso en el editor de código fuente.

## <a name="see-also"></a>Consulte también
- [Depuración de aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Cambio a otro subproceso durante la depuración](../debugger/how-to-switch-to-another-thread-while-debugging.md)
