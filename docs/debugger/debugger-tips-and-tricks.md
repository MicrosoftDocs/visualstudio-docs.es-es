---
title: Sugerencias y trucos del depurador de Visual Studio
description: Obtenga información sobre algunas de las características menos conocidas compatibles con el depurador de Visual Studio
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
ms.openlocfilehash: b67722884a675dd991cad608ca22cf277e2d6777
ms.sourcegitcommit: 498e39e89a89ad7bf9dcb0617424fff999b1c3b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/21/2018
ms.locfileid: "36303086"
---
# <a name="learn-productivity-tips-and-tricks-for-the-debugger-in-visual-studio"></a>Obtenga información sobre sugerencias de productividad y trucos del depurador de Visual Studio

Lea este tema para aprender algunas sugerencias de productividad y trucos para el depurador de Visual Studio. Para conocer las características básicas del depurador, vea [Guía de características del depurador](../debugger/debugger-feature-tour.md). En este tema, trataremos algunas áreas que no están incluidos en la Guía de características.

## <a name="pin-data-tips"></a>Sugerencias de datos de PIN

Si con frecuencia el mouse sobre sugerencias de datos durante la depuración, puede anclar la sugerencia de datos para la variable para tener acceso rápido. La variable permanece anclada incluso después de reiniciar. Para anclar la información sobre datos, haga clic en el icono de anclaje al mantener el mouse sobre él. Puede anclar varias variables.

![Anclar una sugerencia de datos](../debugger/media/dbg-tips-data-tips-pinned.png "PinningDataTip")

## <a name="edit-your-code-and-continue-debugging-c-vb-c"></a>El código de editar y continuar con la depuración (C#, VB, C++)

En la mayoría de los idiomas compatible con Visual Studio, puede editar el código en el medio de una sesión de depuración y continuar con la depuración. Para usar esta característica, haga clic en el código con el cursor mientras está en pausa en el depurador, realizar ediciones y presione **F5**, **F10**, o **F11** para continuar la depuración.

![Editar y continuar con la depuración](../debugger/media/dbg-tips-edit-and-continue.gif "EditAndContinue")

Para obtener más información sobre el uso de la característica y las limitaciones de características, consulte [editar y continuar](../debugger/edit-and-continue.md).

## <a name="debug-issues-that-are-hard-to-reproduce"></a>Depurar los problemas que son difíciles de reproducir

Si es difícil o requiere tiempo volver a crear un estado determinado en la aplicación, considere la posibilidad de si el uso de un punto de interrupción condicional puede ayudar. Puede usar [puntos de interrupción condicionales](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) y filtrar los puntos de interrupción para evitar interrumpir el código de la aplicación hasta que la aplicación entra en un estado deseado (por ejemplo, un estado en el que una variable está almacenando datos incorrectos). Puede establecer las condiciones de uso de expresiones, los filtros, recuentos de visitas y así sucesivamente.

#### <a name="to-create-a-conditional-breakpoint"></a>Para crear un punto de interrupción condicional

1. Haga clic en un icono de punto de interrupción (el círculo rojo) y elija **condiciones**.

2. En el **configuración de punto de interrupción** ventana, escriba una expresión.

    ![Punto de interrupción condicional](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

3. Si está interesado en otro tipo de condición, seleccione **filtro** en lugar de **expresión condicional** en el **configuración de punto de interrupción** cuadro de diálogo y, después, siga las sugerencias de filtro.

## <a name="change-the-execution-flow"></a>Cambiar el flujo de ejecución

Con el depurador pausó en una línea de código, use el mouse para captar el puntero de flecha amarilla en la parte izquierda. Mueva el puntero de flecha amarilla a un punto diferente en la ruta de acceso de ejecución de código. A continuación, utilice F5 o un comando de paso para continuar ejecutando la aplicación.

![Mueva el puntero de ejecución](../debugger/media/dbg-tour-move-the-execution-pointer.gif "mover el puntero de ejecución")

Al cambiar el flujo de ejecución, puede hacer cosas como comprobar las rutas de ejecución de código diferente o volver a ejecutar código sin necesidad de reiniciar al depurador.

> [!WARNING]
> A menudo es necesario tener cuidado con esta característica, y verá una advertencia en la información sobre herramientas. Puede ver otras advertencias, demasiado. Mover el puntero no puede revertir la aplicación a un estado anterior de la aplicación.

## <a name="track-an-out-of-scope-object-c-visual-basic"></a>Realizar un seguimiento de un objeto fuera de ámbito (C#, Visual Basic)

Es fácil ver las variables mediante las ventanas del depurador, como la **inspección** ventana. Sin embargo, cuando una variable se sale del ámbito en el **inspección** ventana, es posible que observe que está atenuado. En algunos escenarios de aplicación, puede cambiar el valor de una variable, incluso cuando la variable está fuera del ámbito, y desea verlo estrechamente (por ejemplo, una variable puede recibir recolectado). Puede realizar un seguimiento de la variable mediante la creación de un identificador de objeto para él en el **inspección** ventana.

#### <a name="to-create-an-object-id"></a>Para crear un identificador de objeto

1.  Establezca un punto de interrupción cerca de una variable que se desea realizar un seguimiento.

2.  Iniciar el depurador (**F5**) y detenga el punto de interrupción.

3. Busque la variable en el **variables locales** ventana (**Depurar > Windows > variables locales**), haga clic en la variable y seleccione **Make Object ID**.

    ![Crear un identificador de objeto](../debugger/media/dbg-tips-watch-create-object-id.png "CreateObjectID")
  
4.  Debería ver el símbolo **$** junto con un número en la ventana **Locales** . Esta variable es el identificador de objeto.
  
5.  Haga clic en la variable de Id. de objeto y elija **Agregar inspección**.

Para obtener más información, consulte [crear un identificador de objeto](../debugger/watch-and-quickwatch-windows.md#bkmk_objectIds).

## <a name="view-return-values-for-functions"></a>Ver los valores devueltos para funciones

Para ver los valores devueltos para las funciones, examine las funciones que aparecen en la **automático** ventana mientras se recorre el código. Para ver el valor devuelto para una función, asegúrese de que ya se ha ejecutado la función que le interese (presione **F10** una vez si están detenidos actualmente en la llamada de función). Si se cierra la ventana, utilice **Depurar > Windows > automático** para abrir el **automático** ventana.

![Ventana de autos](../debugger/media/dbg-tips-autos-window.png "AutosWindow")

Además, puede escribir funciones en el **inmediato** ventana para ver los valores devueltos. (Abrirla con **Depurar > Windows > inmediato**.)

![Ventana Inmediato](../debugger/media/dbg-tips-immediate-window.png "ImmediateWindow")

También puede usar [pseudovariables](../debugger/pseudovariables.md) en el **inspección** y **inmediato** ventana, como `$ReturnValue`.

## <a name="string_visualizer"></a>Inspeccionar las cadenas en un visualizador

Cuando se trabaja con cadenas, puede ser útil ver toda la cadena con formato. Para ver un texto sin formato, una cadena JSON, HTML o XML, haga clic en el icono de lupa ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "icono visualizador") al mantener el mouse sobre una variable que contiene un valor de cadena.

![Abrir un visualizador de cadenas](../debugger/media/dbg-tips-string-visualizers.png "OpenStringVisualizer")

Un visualizador de cadenas puede ayudarle a averiguar si una cadena es un formato incorrecto, según el tipo de cadena. Por ejemplo, un espacio en blanco **valor** campo indica la cadena no se reconoce el tipo de visualizador. Para obtener más información, consulte [cuadro de diálogo del visualizador de cadena](../debugger/string-visualizer-dialog-box.md).

![Visualizador de cadenas JSON](../debugger/media/dbg-tips-string-visualizer-json.png "JSONStringVisualizer")

Para algunos otros tipos como objetos WPF que aparecen en las ventanas del depurador, también puede abrir los visualizadores.

## <a name="break-into-code-on-handled-exceptions"></a>Interrumpir el código en las excepciones controladas

El depurador interrumpe el código en excepciones no controladas. Sin embargo, se tratan las excepciones (por ejemplo, las excepciones que se producen dentro de un `try/catch` bloque) también puede ser una fuente de errores y desee investigar cuando se producen. Puede configurar el depurador para interrumpir el código para las excepciones controladas también mediante la configuración de opciones en el **configuración de excepciones** cuadro de diálogo. Abra este cuadro de diálogo eligiendo **Depurar > Windows > configuración de excepciones**.

El **configuración de excepciones** cuadro de diálogo le permite indicar al depurador para interrumpir el código en excepciones específicas. En la ilustración siguiente, el depurador interrumpe el código cada vez que un `System.NullReferenceException` se produce. Para obtener más información, consulte [administrar excepciones](../debugger/managing-exceptions-with-the-debugger.md).

![Cuadro de diálogo de configuración de excepciones](../debugger/media/dbg-tips-exception-settings.png "ExceptionSettingsDialogBox")

## <a name="debug-deadlocks-and-race-conditions"></a>Depurar los interbloqueos y condiciones de carrera

Si tiene que depurar los tipos de problemas que son comunes a las aplicaciones multiproceso, a menudo resulta útil para ver la ubicación de los subprocesos durante la depuración. Puede hacerlo fácilmente mediante el **Mostrar subprocesos en código fuente** botón.

#### <a name="to-show-threads-in-your-source-code"></a>Para mostrar los subprocesos en el código fuente

1.  Durante la depuración, haga clic en el **Mostrar subprocesos en código fuente** botón ![Mostrar subprocesos en código fuente](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker") en el **depurar** barra de herramientas.
  
2.  Examine el margen interno izquierdo de la ventana. En esta línea, verá un *marcador de subproceso* icono ![marcador de subproceso](../debugger/media/dbg-thread-marker.png "ThreadMarker") que es similar a dos hilos. El marcador de subproceso indica que un subproceso se ha detenido en esa ubicación.

    Tenga en cuenta que un marcador de subproceso es posible que se ocultan parcialmente por un punto de interrupción.
  
3.  Desplace el puntero sobre el marcador de subproceso. Aparece la Información sobre datos. En ella se indican el nombre y el número de id. de subproceso de cada subproceso detenido.

    También puede ver la ubicación de los subprocesos en la [ventana Pilas paralelas](../debugger/get-started-debugging-multithreaded-apps.md).

## <a name="examine-payloads-for-web-services-and-network-resources-uwp"></a>Examine las cargas para servicios web y los recursos de red (UWP)

En aplicaciones UWP, puede analizar las operaciones de red realizadas mediante la `Windows.Web.Http` API. Puede usar esta herramienta para ayudar a depurar los servicios web y los recursos de red. Para usar la herramienta, seleccione **Depurar > Performance Profiler**. Seleccione **red**y, a continuación, elija **iniciar**. En la aplicación, recorra el escenario que use `Windows.Web.Http` y, después, seleccione **Detener recolección** para generar el informe.

![Uso de la herramienta de generación de perfiles de red](../profiling/media/prof-tour-network-usage.png "NetworkUsageProfTool")

Seleccione una operación en la vista de resumen para ver más detalles.

![Información detallada en la herramienta de uso de la red](../profiling/media/prof-tour-network-usage-details.png "DetailedViewNetworkUsage")

Para obtener más información, vea [Network Usage](../profiling/network-usage.md) (Uso de red).

## <a name="get-more-familiar-with-how-the-debugger-attaches-to-your-app"></a>Familiarizarse con cómo el depurador se asocia a la aplicación

Para asociar a la aplicación en ejecución, el depurador carga los archivos de símbolos (.pdb) generados para la misma versión exacta de la aplicación que está intentando depurar. En algunos escenarios, algunos conocimientos de los archivos de símbolos pueden resultar útil. Puede examinar cómo Visual Studio carga los archivos de símbolos mediante el **módulos** ventana.

Abra el **módulos** ventana durante la depuración seleccionando **Depurar > Windows > módulos**. El **módulos** ventana puede indicarle qué módulos el depurador se trata como código de usuario, o [ *mi código*](../debugger/just-my-code.md)y el símbolo de estado para el módulo de carga. En la mayoría de los escenarios, el depurador busca automáticamente los archivos de símbolos para el código de usuario, pero si desea ir a (o depurar) código de .NET framework, código del sistema o código de la biblioteca de terceros, se requieren pasos adicionales para obtener los archivos de símbolos correctos.

![Ver información de símbolos en la ventana módulos](../debugger/media/dbg-tips-modules-window.png "ViewSymbolInformation")

Puede cargar información de símbolos directamente desde el **módulos** ventana con el botón secundario y eligiendo **cargar símbolos**.

En ocasiones, los desarrolladores de aplicaciones distribuyen aplicaciones sin los archivos de símbolos correspondientes (para reducir la superficie), pero mantener una copia del símbolo de coincidencia de archivos para la compilación para que puede depurar una versión posterior.

Para averiguar cómo el depurador clasifica el código como código de usuario, consulte [solo mi código](../debugger/just-my-code.md). Para obtener más información acerca de los archivos de símbolos, vea [especificar archivos de código fuente y símbolos (.pdb) en el depurador de Visual Studio](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="learn-more"></a>Más información

Para otras recomendaciones y trucos y obtener información más detallada, vea estas entradas de blog:

- [7 ataques conocidos menor para la depuración en Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/2017/06/26/7-lesser-known-hacks-for-debugging-in-visual-studio/)
- [7 gemas ocultas de Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/2017/10/05/7-hidden-gems-in-visual-studio-2017/)

## <a name="see-also"></a>Vea también
[Métodos abreviados de teclado](../ide/tips-and-tricks-for-visual-studio.md)
