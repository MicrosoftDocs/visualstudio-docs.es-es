---
title: Sugerencias y trucos en el depurador
description: Obtenga información sobre algunas de las características menos conocidas compatibles con el depurador de Visual Studio
ms.custom: seodec18
ms.date: 06/15/2018
ms.topic: conceptual
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 5262d8b1-2648-429e-85d5-90fcaadfb362
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bf8d6df020694bb10fe4f3f051551056549d5673
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301180"
---
# <a name="learn-productivity-tips-and-tricks-for-the-debugger-in-visual-studio"></a>Obtenga información sobre sugerencias y trucos de productividad para el depurador en Visual Studio

Lea este tema para obtener información sobre algunas sugerencias y trucos de productividad para el depurador de Visual Studio. Para obtener las características básicas del depurador, vea [Primer vistazo al depurador](../debugger/debugger-feature-tour.md). En este tema, se abordarán algunas áreas que no se incluyen en el recorrido por las características.

## <a name="pin-data-tips"></a>Anclaje de sugerencias de datos

Si habitualmente mantiene el mouse sobre las sugerencias de datos durante la depuración, es posible que quiera anclar la sugerencia de datos de la variable para obtener un acceso rápido. La variable permanece anclada incluso después de reiniciar. Para anclar la sugerencia de datos, haga clic en el icono de anclaje mientras mantiene el mouse sobre él. Puede anclar varias variables.

![Anclado de una sugerencia de datos](../debugger/media/dbg-tips-data-tips-pinned.png "PinningDataTip")

## <a name="edit-your-code-and-continue-debugging-c-vb-c"></a>Edición del código y continuación de la depuración (C#, VB, C++)

En la mayoría de los lenguajes compatibles con Visual Studio, puede editar el código en medio de una sesión de depuración y continuar con la depuración. Para usar esta característica, haga clic en el código con el cursor mientras está en pausa en el depurador, realice las ediciones y presione **F5**, **F10** o **F11** para continuar con la depuración.

![Edición de código y depuración continua](../debugger/media/dbg-tips-edit-and-continue.gif "EditAndContinue")

Para obtener más información sobre el uso de la característica y las limitaciones de esta, consulte [Editar y continuar](../debugger/edit-and-continue.md).

## <a name="edit-xaml-code-and-continue-debugging"></a>Edición de código XAML y continuación de la depuración

Para modificar el código XAML durante una sesión de depuración, consulte [Escribir y depurar código XAML en ejecución con la recarga frecuente de XAML](../xaml-tools/xaml-hot-reload.md).

## <a name="debug-issues-that-are-hard-to-reproduce"></a>Incidencias de depuración que son difíciles de reproducir

Si es difícil o se tarda demasiado en volver a crear un estado determinado en la aplicación, considere si el uso de un punto de interrupción condicional puede resultar útil. Puede usar [puntos de interrupción condicionales](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) y filtrar los puntos de interrupción para evitar la interrupción del código de la aplicación hasta que la aplicación entre en un estado deseado (por ejemplo, un estado en el que una variable almacena datos incorrectos). Puede establecer las condiciones mediante expresiones, filtros, recuentos de visitas, etc.

#### <a name="to-create-a-conditional-breakpoint"></a>Para crear un punto de interrupción condicional

1. Haga clic con el botón derecho en el icono de un punto de interrupción (la esfera de color rojo) y elija **Condiciones**.

2. En la ventana **Configuración del punto de interrupción**, escriba una expresión.

    ![Punto de interrupción condicional](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

3. Si le interesa otro tipo de condición, seleccione **Filtro** en lugar de **Expresión condicional** en el cuadro de diálogo **Configuración del punto de interrupción** y, después, siga las sugerencias de filtro.

## <a name="configure-the-data-to-show-in-the-debugger"></a>Configuración de los datos que se van a mostrar en el depurador

Para C#, Visual Basic y C++ (solo código de C++/CLI), puede indicar al depurador qué información se debe mostrar mediante el atributo [DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md). Para el código de C++, puede hacer lo mismo con las [visualizaciones de Natvis](create-custom-views-of-native-objects.md).

## <a name="change-the-execution-flow"></a>Cambio del flujo de ejecución

Con el depurador en pausa en una línea de código, use el mouse para seleccionar el puntero de flecha amarillo situado a la izquierda. Mueva el puntero de flecha amarillo a otro punto en la ruta de ejecución del código. Después, presione F5 o un comando de paso para continuar con la ejecución de la aplicación.

![Movimiento del puntero de ejecución](../debugger/media/dbg-tour-move-the-execution-pointer.gif "Movimiento del puntero de ejecución")

Al cambiar el flujo de ejecución, puede, por ejemplo, comprobar las diferentes rutas de ejecución de código o volver a ejecutar código sin tener que reiniciar el depurador.

> [!WARNING]
> A menudo es necesario tener cuidado con esta característica, ya que puede ser que vea una advertencia en la información en pantalla. También puede ser que reciba otras advertencias. El hecho de mover el puntero no permite revertir la aplicación a un estado anterior.

## <a name="track-an-out-of-scope-object-c-visual-basic"></a>Seguimiento de un objeto fuera de ámbito (C#, Visual Basic)

Es fácil ver las variables mediante ventanas del depurador, como la ventana **Inspección**. Pero cuando una variable sale del ámbito en la ventana **Inspección**, es posible que observe que está atenuada. En algunos escenarios de aplicación, el valor de una variable puede cambiar incluso cuando la variable está fuera del ámbito, y es posible que quiera verla con más detalle (por ejemplo, una variable puede ser objeto de la recolección de elementos no utilizados). Puede realizar el seguimiento de la variable si crea un identificador de objeto para ella en la ventana **Inspección**.

#### <a name="to-create-an-object-id"></a>Para crear un identificador de objeto

1. Establezca un punto de interrupción cerca de una variable de la que quiera realizar el seguimiento.

2. Inicie el depurador (**F5**) y deténgase en el punto de interrupción.

3. Busque la variable en la ventana **Variables locales** (**Depuración > Ventanas > Variables locales**), haga clic con el botón derecho en la variable y seleccione **Crear el identificador del objeto**.

    ![Creación de un identificador del objeto](../debugger/media/dbg-tips-watch-create-object-id.png "CreateObjectID")

4. Debería ver el símbolo **$** junto con un número en la ventana **Locales** . Esta variable es el identificador del objeto.

5. Haga clic con el botón derecho en la variable de identificador del objeto y elija **Agregar inspección**.

Para obtener más información, vea [Creación de un identificador del objeto](../debugger/watch-and-quickwatch-windows.md#bkmk_objectIds).

## <a name="view-return-values-for-functions"></a>Visualización de valores devueltos para funciones

Para ver los valores devueltos para las funciones, examine las funciones que aparecen en la ventana **Automático** mientras ejecuta el código paso a paso. Para ver el valor devuelto de una función, asegúrese de que la función que le interesa ya se haya ejecutado (presione **F10** una vez si está detenido actualmente en la llamada de función). Si la ventana está cerrada, use **Depurar > Ventanas > Automático** para abrir la ventana **Automático**.

![Ventana Automático](../debugger/media/dbg-tips-autos-window.png "AutosWindow")

Además, puede escribir funciones en la ventana **Inmediato** para ver los valores devueltos. (Para abrirla, seleccione **Depurar > Ventanas > Inmediato**).

![Ventana Inmediato](../debugger/media/dbg-tips-immediate-window.png "ImmediateWindow")

También puede usar [pseudovariables](../debugger/pseudovariables.md) en las ventanas **Inspección** e **Inmediato**, como `$ReturnValue`.

## <a name="inspect-strings-in-a-visualizer"></a><a name="string_visualizer"></a>Inspección de cadenas en un visualizador

Cuando se trabaja con cadenas, puede resultar útil ver toda la cadena con formato. Para ver una cadena de texto sin formato, XML, HTML o JSON, haga clic en el icono de lupa ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Icono del visualizador") mientras mantiene el mouse sobre una variable que contenga un valor de cadena.

![Apertura de un visualizador de cadenas](../debugger/media/dbg-tips-string-visualizers.png "OpenStringVisualizer")

Un visualizador de cadenas puede ayudarle a determinar si una cadena tiene un formato incorrecto, en función del tipo de cadena. Por ejemplo, un campo **Valor** en blanco indica que el tipo de visualizador no reconoce la cadena. Para obtener más información, vea [Visualizador de cadenas (cuadro de diálogo)](../debugger/string-visualizer-dialog-box.md).

![Visualizador de cadenas JSON](../debugger/media/dbg-tips-string-visualizer-json.png "JSONStringVisualizer")

En el caso de otros tipos, como los objetos DataSet y DataTable que aparecen en las ventanas del depurador, también puede abrir un visualizador integrado.

## <a name="break-into-code-on-handled-exceptions"></a>Interrupción del código en excepciones controladas

El depurador interrumpe el código en las excepciones no controladas. Pero las excepciones controladas (como las que se producen dentro de un bloque `try/catch`) también pueden ser una fuente de errores y es posible que quiera investigarlas cuando se produzcan. Puede configurar el depurador para que interrumpa el código para excepciones controladas, además de establecer opciones en el cuadro de diálogo **Configuración de excepciones**. Para abrir este cuadro de diálogo, elija **Depurar > Ventanas > Configuración de excepciones**.

En el cuadro de diálogo **Configuración de excepciones** puede indicar al depurador que interrumpa el código en excepciones concretas. En la ilustración siguiente, el depurador interrumpe el código cada vez que se produce una excepción `System.NullReferenceException`. Para obtener más información, vea [Administración de excepciones](../debugger/managing-exceptions-with-the-debugger.md).

![Cuadro de diálogo Configuración de excepciones](../debugger/media/dbg-tips-exception-settings.png "ExceptionSettingsDialogBox")

## <a name="debug-deadlocks-and-race-conditions"></a>Depuración de interbloqueos y condiciones de carrera

Si tiene que depurar los tipos de incidencias comunes a las aplicaciones multiproceso, a menudo resulta útil ver la ubicación de los subprocesos durante la depuración. Puede hacerlo fácilmente con el botón **Mostrar subprocesos en código fuente**.

#### <a name="to-show-threads-in-your-source-code"></a>Para mostrar los subprocesos en el código fuente

1. Durante la depuración, haga clic en el botón **Mostrar subprocesos en código fuente** ![Mostrar subprocesos en código fuente](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker") en la barra de herramientas **Depurar**.

2. Examine el margen interno izquierdo de la ventana. En esta línea, verá un icono de *marcador de subproceso* ![Thread Marker](../debugger/media/dbg-thread-marker.png "ThreadMarker") que se parece a dos hilos de coser. El marcador de subproceso indica que un subproceso se ha detenido en esa ubicación.

    Observe que un punto de interrupción puede ocultar parcialmente un marcador de subproceso.

3. Desplace el puntero sobre el marcador de subproceso. Aparece la Información sobre datos. En ella se indican el nombre y el número de id. de subproceso de cada subproceso detenido.

    También puede ver la ubicación de los subprocesos en la [ventana Pilas paralelas](../debugger/get-started-debugging-multithreaded-apps.md).

::: moniker range="vs-2017"
## <a name="examine-payloads-for-web-services-and-network-resources-uwp"></a>Examen de cargas para servicios web y recursos de red (UWP)

En las aplicaciones para UWP, puede analizar las operaciones de red realizadas mediante la API `Windows.Web.Http`. Puede usar esta herramienta para facilitar la depuración de los servicios web y los recursos de red. Para usar la herramienta, seleccione **Depurar > Generador de perfiles de rendimiento**. Seleccione **Red** y después **Iniciar**. En la aplicación, recorra el escenario que use `Windows.Web.Http` y, después, seleccione **Detener recolección** para generar el informe.

![Herramienta de generación de perfiles de uso de red](../profiling/media/prof-tour-network-usage.png "NetworkUsageProfTool")

Seleccione una operación en la vista de resumen para ver más detalles.

![Información detallada en la herramienta Uso de red](../profiling/media/prof-tour-network-usage-details.png "DetailedViewNetworkUsage")

Para obtener más información, vea [Network Usage](../profiling/network-usage.md) (Uso de red).
::: moniker-end

## <a name="get-more-familiar-with-how-the-debugger-attaches-to-your-app-c-c-visual-basic-f"></a><a name="modules_window"></a> Familiarizarse con el modo en que el depurador se asocia a la aplicación (C#, C++, Visual Basic, F#)

Para adjuntar a la aplicación en ejecución, el depurador carga los archivos de símbolos (.pdb) generados para la misma compilación exacta de la aplicación que se intenta depurar. En algunos escenarios, un pequeño conocimiento sobre los archivos de símbolos puede ser útil. Puede examinar cómo carga Visual Studio los archivos de símbolos mediante la ventana **Módulos**.

Para abrir la ventana **Módulos** durante la depuración, seleccione **Depurar > Ventanas > Módulos**. La ventana **Módulos** puede indicar qué módulos trata el depurador como código de usuario, o bien [*Mi código*](../debugger/just-my-code.md), y el estado de carga de símbolos para el módulo. En la mayoría de los escenarios, el depurador busca automáticamente el código de usuario en los archivos de símbolos, pero si quiere depurar paso a paso por instrucciones código de .NET, del sistema o de bibliotecas de terceros, se necesitan pasos adicionales para obtener los archivos de símbolos correctos.

![Visualización de información de símbolos en la ventana Módulos](../debugger/media/dbg-tips-modules-window.png "ViewSymbolInformation")

Puede cargar la información de símbolos directamente desde la ventana **Módulos** si hace clic con el botón derecho y selecciona **Cargar símbolos**.

En ocasiones, los desarrolladores de aplicaciones las envían sin los archivos de símbolos coincidentes (para reducir la superficie), pero conservan una copia de los archivos de símbolos coincidentes de la compilación para más adelante poder depurar una versión de lanzamiento.

Para averiguar cómo clasifica el depurador el código como código de usuario, vea [Solo mi código](../debugger/just-my-code.md). Para obtener más información sobre los archivos de símbolos, vea [Especificación de archivos de código fuente y símbolos (.pdb) en el depurador de Visual Studio](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="learn-more"></a>Más información

Para obtener sugerencias y trucos adicionales, e información más detallada, vea estas entradas de blog:

- [Siete modificaciones menos conocidas para la depuración en Visual Studio](https://devblogs.microsoft.com/visualstudio/7-lesser-known-hacks-for-debugging-in-visual-studio/)
- [Siete joyas ocultas en Visual Studio](https://devblogs.microsoft.com/visualstudio/7-hidden-gems-in-visual-studio-2017/)

## <a name="see-also"></a>Vea también

[Métodos abreviados de teclado](../ide/productivity-shortcuts.md)
