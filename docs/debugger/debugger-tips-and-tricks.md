---
title: Sugerencias y trucos en el depurador de Visual Studio
description: Obtenga información acerca de sugerencias de productividad para que el depurador de Visual Studio
ms.custom: ''
ms.date: 06/15/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 5262d8b1-2648-429e-85d5-90fcaadfb362
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bb4fb2c32f74a764e092e0e6f65685a358d64f54
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31927287"
---
# <a name="learn-productivity-tips-and-tricks-for-the-debugger-in-visual-studio"></a>Obtenga información acerca de productividad sugerencias y trucos para el depurador de Visual Studio

Lea este tema para obtener información sobre algunos trucos y sugerencias de productividad para que el depurador de Visual Studio. Para obtener una visión de las características básicas del depurador, vea [depurador paseo](../debugger/debugger-feature-tour.md). En este tema, trataremos algunas áreas que no están incluidos en el paseo.

## <a name="pin-data-tips"></a>Sugerencias de datos de PIN

Si con frecuencia sitúa sobre sugerencias de datos durante la depuración, puede que desee anclar la sugerencia de datos para la variable disponer de acceso rápido. La variable sigue siendo anclada incluso después de reiniciar. Para anclar la información sobre datos, haga clic en el icono de anclaje mientras se mantiene el mouse sobre él. Puede anclar varias variables.

![Fijar una sugerencia de datos](../debugger/media/dbg-tips-data-tips-pinned.png "PinningDataTip")

## <a name="edit-your-code-and-continue-debugging-c-vb-c"></a>Modificar el código y continuar con la depuración (C#, VB, C++)

En la mayoría de los idiomas compatible con Visual Studio, puede modificar el código en el medio de una sesión de depuración y continuar con la depuración. Para usar esta característica, haga clic en el código con el cursor mientras está en pausa en el depurador, asegúrese de ediciones y presione **F5**, **F10**, o **F11** para continuar la depuración.

![Editar y continuar con la depuración](../debugger/media/dbg-tips-edit-and-continue.gif "EditAndContinue")

Para obtener más información sobre el uso de la característica y las limitaciones de características, vea [editar y continuar](../debugger/edit-and-continue.md).

## <a name="debug-issues-that-are-hard-to-reproduce"></a>Depurar los problemas que son difíciles de reproducir

Si es difícil o requiere tiempo volver a crear un estado determinado en la aplicación, tenga en cuenta si el uso de un punto de interrupción condicional puede ayudar. Puede usar [puntos de interrupción condicionales](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) y filtrar los puntos de interrupción para evitar interrumpir el código de la aplicación hasta que la aplicación entra en un estado deseado (por ejemplo, un estado en el que una variable está almacenando datos incorrectos). Puede establecer condiciones que usan expresiones, filtros, recuentos de visitas y así sucesivamente.

#### <a name="to-create-a-conditional-breakpoint"></a>Para crear un punto de interrupción condicional

1. Haga clic en un icono de punto de interrupción (el círculo rojo) y elija **condiciones**.

2. En el **configuración de punto de interrupción** ventana, escriba una expresión.

    ![Punto de interrupción condicional](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

3. Si está interesado en otro tipo de condición, seleccione **filtro** en lugar de **expresión condicional** en el **configuración de punto de interrupción** cuadro de diálogo y, a continuación, siga las sugerencias de filtro.

## <a name="change-the-execution-flow"></a>Cambiar el flujo de ejecución

Con el depurador está en pausa en una línea de código, use el mouse para arrastrar el puntero de flecha amarilla en la parte izquierda. Mueva el puntero de flecha amarilla en otro punto de la ruta de acceso de ejecución de código. A continuación, utilice F5 o un comando de paso para continuar ejecutando la aplicación.

![Mueva el puntero de ejecución](../debugger/media/dbg-tour-move-the-execution-pointer.gif "mover el puntero de ejecución")

Al cambiar el flujo de ejecución, puede hacer cosas como probar las rutas de acceso de ejecución de código diferente o vuelva a ejecutar el código sin necesidad de reiniciar al depurador.

> [!WARNING]
> A menudo necesita tener cuidado con esta característica, y verá una advertencia en la información sobre herramientas. Puede ver otras advertencias, demasiado. Mueva el puntero, no puede revertir la aplicación a un estado anterior de la aplicación.

## <a name="track-an-out-of-scope-object-c-visual-basic"></a>Realizar un seguimiento de un objeto fuera de ámbito (C#, Visual Basic)

Es fácil ver variables con ventanas del depurador como el **inspección** ventana. Sin embargo, cuando una variable se sale del ámbito en el **inspección** ventana, puede observar que está atenuado. En algunos escenarios de aplicación, puede cambiar el valor de una variable incluso cuando la variable está fuera del ámbito, y desea verlo estrechamente (por ejemplo, una variable puede obtener recolección). Puede realizar un seguimiento de la variable mediante la creación de un identificador de objeto para él en el **inspección** ventana.

#### <a name="to-create-an-object-id"></a>Para crear un identificador de objeto

1.  Establecer un punto de interrupción cerca de una variable que se desea realizar un seguimiento.

2.  Iniciar el depurador (**F5**) y detenga en el punto de interrupción.

3. Encuentra la variable en el **locales** ventana (**Depurar > Windows > variables locales**), haga clic en la variable y seleccione **crear el identificador del objeto**.

    ![Crear un identificador de objeto](../debugger/media/dbg-tips-watch-create-object-id.png "CreateObjectID")
  
4.  Debería ver el símbolo **$** junto con un número en la ventana **Locales** . Esta variable es el identificador de objeto.
  
5.  Haga clic en la variable de Id. de objeto y elija **Agregar inspección**.

Para obtener más información, consulte [crear un identificador de objeto](../debugger/watch-and-quickwatch-windows.md#bkmk_objectIds).

## <a name="view-return-values-for-functions"></a>Ver los valores devueltos para las funciones

Para ver los valores devueltos para las funciones, examine las funciones que aparecen en la **automático** ventana mientras se recorre el código. Para ver el valor devuelto para una función, asegúrese de que ya ha ejecutado la función que le interesen (presione **F10** una vez si actualmente se detiene en la llamada de función). Si se cierra la ventana, utilice **Depurar > Windows > automático** para abrir el **automático** ventana.

![Automático ventana](../debugger/media/dbg-tips-autos-window.png "AutosWindow")

Además, puede escribir funciones en el **inmediato** ventana para ver los valores devueltos. (Ábralos con **Depurar > Windows > inmediato**.)

![Inmediato (ventana)](../debugger/media/dbg-tips-immediate-window.png "ImmediateWindow")

También puede usar [pseudovariables](../debugger/pseudovariables.md) en el **inspección** y **inmediato** ventana, como `$ReturnValue`.

## <a name="string_visualizer"></a>Inspeccionar las cadenas en un visualizador

Cuando se trabaja con cadenas, puede resultar útil ver toda la cadena con formato. Para ver un texto sin formato, la cadena XML, HTML o JSON, haga clic en el icono de lupa ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "icono visualizador") manteniendo el mouse sobre una variable que contiene un valor de cadena.

![Abrir un visualizador de cadenas](../debugger/media/dbg-tips-string-visualizers.png "OpenStringVisualizer")

Un visualizador de cadenas puede ayudarle a determinar si una cadena con formato incorrecto, dependiendo del tipo de cadena. Por ejemplo, un espacio en blanco **valor** campo indica la cadena no se reconoce el tipo del visualizador. Para obtener más información, consulte [cuadro de diálogo del visualizador de cadena](../debugger/string-visualizer-dialog-box.md).

![Visualizador de cadenas JSON](../debugger/media/dbg-tips-string-visualizer-json.png "JSONStringVisualizer")

Para algunos otros tipos, como los objetos WPF que aparecen en las ventanas del depurador, también puede abrir los visualizadores.

## <a name="break-into-code-on-handled-exceptions"></a>Interrumpir el código en las excepciones administradas

El depurador interrumpe el código en excepciones no controladas. Sin embargo, controla las excepciones (por ejemplo, las excepciones que se producen dentro de un `try/catch` bloque) también puede ser un origen de los errores y puede que desee investigar cuando se producen. Puede configurar el depurador para interrumpir el código para las excepciones administradas también mediante la configuración de opciones en la **configuración de excepciones** cuadro de diálogo. Abrir este cuadro de diálogo seleccionando **Depurar > Windows > configuración de excepciones**.

El **configuración de excepciones** cuadro de diálogo le permite indicar al depurador para interrumpir el código en excepciones específicas. En la ilustración siguiente, el depurador interrumpe el código cada vez que un `System.NullReferenceException` se produce. Para obtener más información, consulte [administrar excepciones](../debugger/managing-exceptions-with-the-debugger.md).

![Cuadro de diálogo de configuración de excepción](../debugger/media/dbg-tips-exception-settings.png "ExceptionSettingsDialogBox")

## <a name="debug-deadlocks-and-race-conditions"></a>Depurar interbloqueos y condiciones de carrera

Si tiene que depurar los tipos de problemas que son comunes a las aplicaciones multiproceso, a menudo es útil para ver la ubicación de subprocesos durante la depuración. Puede hacer esto fácilmente mediante la **Mostrar subprocesos en código fuente** botón.

#### <a name="to-show-threads-in-your-source-code"></a>Para mostrar subprocesos en el código fuente

1.  Durante la depuración, haga clic en el **Mostrar subprocesos en código fuente** botón ![Mostrar subprocesos en código fuente](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker") en el **depurar** barra de herramientas.
  
2.  Examine el margen interno izquierdo de la ventana. En esta línea, verá un *marcador de subproceso* icono ![marcador de subproceso](../debugger/media/dbg-thread-marker.png "ThreadMarker") que es similar a dos hilos. El marcador de subproceso indica que un subproceso se ha detenido en esa ubicación.

    Tenga en cuenta que un marcador de subproceso puede ocultarse parcialmente por un punto de interrupción.
  
3.  Desplace el puntero sobre el marcador de subproceso. Aparece la Información sobre datos. En ella se indican el nombre y el número de id. de subproceso de cada subproceso detenido.

    También puede ver la ubicación de subprocesos en la [la ventana Pilas paralelas](../debugger/get-started-debugging-multithreaded-apps.md).

## <a name="examine-payloads-for-web-services-and-network-resources-uwp"></a>Examine las cargas de servicios web y recursos de red (UWP)

En las aplicaciones UWP, puede analizar las operaciones de red realizadas mediante la `Windows.Web.Http` API. Puede utilizar esta herramienta para ayudar a depurar los servicios web y recursos de red. Para usar la herramienta, seleccione **Depurar > Generador de perfiles de rendimiento**. Seleccione **red**y, a continuación, elija **iniciar**. En la aplicación, recorra el escenario que use `Windows.Web.Http` y, después, seleccione **Detener recolección** para generar el informe.

![Uso de la herramienta de generación de perfiles de red](../profiling/media/prof-tour-network-usage.png "NetworkUsageProfTool")

Seleccione una operación en la vista de resumen para ver más detalles.

![Información detallada en la herramienta de uso de la red](../profiling/media/prof-tour-network-usage-details.png "DetailedViewNetworkUsage")

Para obtener más información, vea [Network Usage](../profiling/network-usage.md) (Uso de red).

## <a name="get-more-familiar-with-how-the-debugger-attaches-to-your-app"></a>Obtener más familiarizado con cómo se asocia el depurador a la aplicación

Para asociar a la aplicación en ejecución, el depurador carga los archivos de símbolos (.pdb) generados para la misma versión exacta de la aplicación que está intentando depurar. En algunos escenarios, un poco conocimiento de los archivos de símbolos puede resultar útil. Puede examinar la forma en que Visual Studio carga los archivos de símbolos mediante el **módulos** ventana.

Abra la **módulos** ventana mientras se depura seleccionando **Depurar > Windows > módulos**. El **módulos** ventana puede indicar qué módulos que el depurador se trata como código de usuario, o [ *mi código*](../debugger/just-my-code.md)y el símbolo de estado para el módulo de carga. En la mayoría de los escenarios, el depurador busca automáticamente archivos de símbolos de código de usuario, pero si desea depurar paso a paso (o depurar) código de .NET framework, el código de sistema o el código de la biblioteca de terceros, pasos adicionales necesarios para obtener los archivos de símbolos correctos.

![Ver información de símbolos en la ventana módulos](../debugger/media/dbg-tips-modules-window.png "ViewSymbolInformation")

Puede cargar información de símbolos directamente desde el **módulos** ventana, con el botón secundario y elija **cargar símbolos**.

En ocasiones, los desarrolladores de aplicaciones distribuyen aplicaciones sin archivos de símbolos coincidentes (para reducir la superficie), pero mantener una copia del símbolo de coincidencia de archivos de la compilación para que puedan depurar una versión de lanzamiento más adelante.

Para averiguar cómo el depurador clasifica el código como código de usuario, consulte [solo mi código](../debugger/just-my-code.md). Para obtener más información acerca de los archivos de símbolos, vea [especificar archivos de código fuente y símbolos (.pdb) en el depurador de Visual Studio](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="learn-more"></a>Más información

Para obtener sugerencias adicionales y trucos e información más detallada, vea estas entradas de blog:

- [7 ataques conocidos menor para la depuración en Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/2017/06/26/7-lesser-known-hacks-for-debugging-in-visual-studio/)
- [7 gems ocultos en Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/2017/10/05/7-hidden-gems-in-visual-studio-2017/)

## <a name="see-also"></a>Vea también
[Métodos abreviados de teclado](../ide/tips-and-tricks-for-visual-studio.md)
