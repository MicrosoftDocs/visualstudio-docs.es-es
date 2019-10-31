---
title: Sugerencias y trucos en el depurador
description: Obtenga información sobre algunas de las características menos conocidas compatibles con el depurador de Visual Studio
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
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2019
ms.locfileid: "73188619"
---
# <a name="learn-productivity-tips-and-tricks-for-the-debugger-in-visual-studio"></a>Obtenga información sobre sugerencias y trucos de productividad para el depurador en Visual Studio

Lea este tema para obtener información sobre algunas sugerencias y trucos de productividad para el depurador de Visual Studio. Para ver las características básicas del depurador, vea [primer vistazo al depurador](../debugger/debugger-feature-tour.md). En este tema, trataremos algunas áreas que no se incluyen en la guía de características.

## <a name="pin-data-tips"></a>Anclar sugerencias de datos

Si con frecuencia mantiene el mouse sobre las sugerencias de datos durante la depuración, es posible que desee anclar la sugerencia de datos de la variable para obtener un acceso rápido. La variable permanece anclada incluso después de reiniciar. Para anclar la información sobre datos, haga clic en el icono de anclaje mientras mantiene el puntero sobre él. Puede anclar varias variables.

![Anclar una sugerencia de datos](../debugger/media/dbg-tips-data-tips-pinned.png "PinningDataTip")

## <a name="edit-your-code-and-continue-debugging-c-vb-c"></a>Edite el código y continúe con laC#depuración C++(, VB,)

En la mayoría de los lenguajes compatibles con Visual Studio, puede editar el código en medio de una sesión de depuración y continuar con la depuración. Para usar esta característica, haga clic en el código con el cursor mientras está en pausa en el depurador, realice las ediciones y presione **F5**, **F10** o **F11** para continuar con la depuración.

![Edición de código y depuración continua](../debugger/media/dbg-tips-edit-and-continue.gif "EditAndContinue")

Para obtener más información sobre el uso de la característica y las limitaciones de esta, consulte [Editar y continuar](../debugger/edit-and-continue.md).

## <a name="edit-xaml-code-and-continue-debugging"></a>Editar código XAML y continuar la depuración

Para modificar el código XAML durante una sesión de depuración, consulte [Escribir y depurar código XAML en ejecución con la recarga frecuente de XAML](../xaml-tools/xaml-hot-reload.md).

## <a name="debug-issues-that-are-hard-to-reproduce"></a>Problemas de depuración que son difíciles de reproducir

Si es difícil o lento volver a crear un estado determinado en la aplicación, considere si el uso de un punto de interrupción condicional puede ser útil. Puede usar [puntos de interrupción condicionales](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) y filtrar puntos de interrupción para evitar la interrupción del código de la aplicación hasta que la aplicación entre en un estado deseado (por ejemplo, un estado en el que una variable almacena datos incorrectos). Puede establecer condiciones mediante expresiones, filtros, recuentos de visitas, etc.

#### <a name="to-create-a-conditional-breakpoint"></a>Para crear un punto de interrupción condicional

1. Haga clic con el botón secundario en un icono de punto de interrupción (la esfera roja) y elija **condiciones**.

2. En la ventana **configuración del punto de interrupción** , escriba una expresión.

    ![Punto de interrupción condicional](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

3. Si está interesado en otro tipo de condición, seleccione **filtrar** en lugar de **expresión condicional** en el cuadro de diálogo **configuración del punto de interrupción** y, a continuación, siga las sugerencias de filtro.

## <a name="configure-the-data-to-show-in-the-debugger"></a>Configurar los datos que se van a mostrar en el depurador

Para C#, Visual Basic y C++ (C++solo en el código/CLI), puede indicar al depurador qué información se debe mostrar mediante el atributo [DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md) . Para C++ el código, puede hacer lo mismo con las [visualizaciones de Natvis](create-custom-views-of-native-objects.md).

## <a name="change-the-execution-flow"></a>Cambio del flujo de ejecución

Con el depurador en pausa en una línea de código, use el mouse para obtener el puntero de flecha amarillo situado a la izquierda. Mueva el puntero de flecha amarillo a un punto diferente en la ruta de acceso de ejecución del código. A continuación, use F5 o un comando STEP para continuar con la ejecución de la aplicación.

![Movimiento del puntero de ejecución](../debugger/media/dbg-tour-move-the-execution-pointer.gif "Movimiento del puntero de ejecución")

Al cambiar el flujo de ejecución, puede, por ejemplo, comprobar las diferentes rutas de ejecución de código o volver a ejecutar código sin tener que reiniciar el depurador.

> [!WARNING]
> A menudo es necesario tener cuidado con esta característica, ya que puede ser que vea una advertencia en la información en pantalla. También puede ser que reciba otras advertencias. Al mover el puntero no se puede revertir la aplicación a un estado anterior de la aplicación.

## <a name="track-an-out-of-scope-object-c-visual-basic"></a>Realizar un seguimiento de un objeto fuera de ámbitoC#(, Visual Basic)

Es fácil ver las variables mediante ventanas del depurador, como la ventana **inspección** . Sin embargo, cuando una variable sale del ámbito en la ventana **inspección** , es posible que observe que está atenuada. En algunos escenarios de aplicación, el valor de una variable puede cambiar incluso cuando la variable está fuera del ámbito, y es posible que desee verla en estrecha profundidad (por ejemplo, una variable puede obtener la recolección de elementos no utilizados). Puede realizar el seguimiento de la variable creando un identificador de objeto para ella en la ventana **inspección** .

#### <a name="to-create-an-object-id"></a>Para crear un identificador de objeto

1. Establezca un punto de interrupción cerca de una variable de la que desee realizar un seguimiento.

2. Inicie el depurador (**F5**) y deténgase en el punto de interrupción.

3. Busque la variable en la ventana **variables locales** (**depurar > Windows > variables locales**), haga clic con el botón derecho en la variable y seleccione **crear ID**. de objeto.

    ![Crear un identificador de objeto](../debugger/media/dbg-tips-watch-create-object-id.png "CreateObjectID")

4. Debería ver el símbolo **$** junto con un número en la ventana **Locales** . Esta variable es el identificador de objeto.

5. Haga clic con el botón derecho en la variable de ID. de objeto y elija **Agregar inspección**.

Para obtener más información, vea [crear un identificador de objeto](../debugger/watch-and-quickwatch-windows.md#bkmk_objectIds).

## <a name="view-return-values-for-functions"></a>Ver valores devueltos para funciones

Para ver los valores devueltos de las funciones, examine las funciones que aparecen en la ventana **automático** mientras se recorre el código. Para ver el valor devuelto de una función, asegúrese de que ya se ha ejecutado la función que le interesa (presione **F10** una vez si está detenido actualmente en la llamada de función). Si la ventana está cerrada, use **Debug > Windows > automático** para abrir la ventana **automático** .

![Ventana Automático](../debugger/media/dbg-tips-autos-window.png "AutosWindow")

Además, puede escribir funciones en la ventana **inmediato** para ver los valores devueltos. (Ábralo mediante **Depurar > Windows > inmediato**).

![Ventana Inmediato](../debugger/media/dbg-tips-immediate-window.png "ImmediateWindow")

También puede usar [pseudovariables](../debugger/pseudovariables.md) en las ventanas **inspección** e **inmediato** , como `$ReturnValue`.

## <a name="string_visualizer"></a>Inspeccionar cadenas en un visualizador

Al trabajar con cadenas, puede resultar útil ver toda la cadena con formato. Para ver una cadena de texto sin formato, XML, HTML o JSON, haga clic en el icono de lupa ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Icono del visualizador") mientras mantiene el puntero sobre una variable que contiene un valor de cadena.

![Abrir un visualizador de cadenas](../debugger/media/dbg-tips-string-visualizers.png "OpenStringVisualizer")

Un visualizador de cadenas puede ayudarle a averiguar si una cadena tiene un formato incorrecto, dependiendo del tipo de cadena. Por ejemplo, un campo de **valor** en blanco indica que el tipo de visualizador no reconoce la cadena. Para obtener más información, vea [cuadro de diálogo visualizador de cadenas](../debugger/string-visualizer-dialog-box.md).

![Visualizador de cadenas JSON](../debugger/media/dbg-tips-string-visualizer-json.png "JSONStringVisualizer")

En el caso de otros tipos, como los objetos DataSet y DataTable que aparecen en las ventanas del depurador, también puede abrir un visualizador integrado.

## <a name="break-into-code-on-handled-exceptions"></a>Interrumpir el código en las excepciones controladas

El depurador se interrumpe en el código en las excepciones no controladas. Sin embargo, las excepciones controladas (como las excepciones que se producen dentro de un bloque `try/catch`) también pueden ser una fuente de errores y es posible que desee investigar cuando se producen. Puede configurar el depurador para que divida en el código para las excepciones controladas también mediante la configuración de opciones en el cuadro de diálogo **configuración de excepciones** . Para abrir este cuadro de diálogo, elija **Depurar > configuración de excepciones de Windows >** .

El cuadro de diálogo **configuración de excepciones** permite indicar al depurador que interrumpa el código en las excepciones específicas. En la ilustración siguiente, el depurador se interrumpe en el código cada vez que se produce un `System.NullReferenceException`. Para obtener más información, consulte [Administración de excepciones](../debugger/managing-exceptions-with-the-debugger.md).

![Cuadro de diálogo Configuración de excepciones](../debugger/media/dbg-tips-exception-settings.png "ExceptionSettingsDialogBox")

## <a name="debug-deadlocks-and-race-conditions"></a>Depurar interbloqueos y condiciones de carrera

Si necesita depurar los tipos de problemas comunes a las aplicaciones multiproceso, a menudo resulta útil ver la ubicación de los subprocesos durante la depuración. Puede hacerlo fácilmente con el botón **Mostrar subprocesos en el origen** .

#### <a name="to-show-threads-in-your-source-code"></a>Para mostrar los subprocesos en el código fuente

1. Durante la depuración, haga clic en el botón **Mostrar subprocesos en el origen** ![Mostrar subprocesos en origen](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker") en la barra de herramientas **depurar** .

2. Examine el margen interno izquierdo de la ventana. En esta línea, verá un ![marcador](../debugger/media/dbg-thread-marker.png "ThreadMarker") de subproceso de icono de *marcador* de subproceso que se parece a dos subprocesos de tela. El marcador de subproceso indica que un subproceso se ha detenido en esa ubicación.

    Observe que un punto de interrupción puede ocultar parcialmente un marcador de subproceso.

3. Desplace el puntero sobre el marcador de subproceso. Aparece la Información sobre datos. En ella se indican el nombre y el número de id. de subproceso de cada subproceso detenido.

    También puede ver la ubicación de los subprocesos en la [ventana pilas paralelas](../debugger/get-started-debugging-multithreaded-apps.md).

::: moniker range="vs-2017"
## <a name="examine-payloads-for-web-services-and-network-resources-uwp"></a>Examen de cargas para servicios web y recursos de red (UWP)

En las aplicaciones UWP, puede analizar las operaciones de red realizadas mediante la API de `Windows.Web.Http`. Puede usar esta herramienta para ayudar a depurar los servicios web y los recursos de red. Para usar la herramienta, seleccione **Depurar > generador de perfiles de rendimiento**. Seleccione **red**y, a continuación, elija **iniciar**. En la aplicación, recorra el escenario que use `Windows.Web.Http` y, después, seleccione **Detener recolección** para generar el informe.

![Herramienta de generación de perfiles de uso de red](../profiling/media/prof-tour-network-usage.png "NetworkUsageProfTool")

Seleccione una operación en la vista de resumen para ver más detalles.

![Información detallada en la herramienta uso de red](../profiling/media/prof-tour-network-usage-details.png "DetailedViewNetworkUsage")

Para obtener más información, vea [Network Usage](../profiling/network-usage.md) (Uso de red).
::: moniker-end

## <a name="modules_window"></a>Familiarícese con el modo en que el depurador se asocia aC#la C++aplicación (, F#, Visual Basic)

Para asociar a la aplicación en ejecución, el depurador carga los archivos de símbolos (. pdb) generados para la misma compilación exacta de la aplicación que está intentando depurar. En algunos escenarios, un pequeño conocimiento de los archivos de símbolos puede ser útil. Puede examinar cómo Visual Studio carga los archivos de símbolos mediante la ventana **módulos** .

Para abrir la ventana **módulos** durante la depuración, seleccione **depurar > módulos de Windows >** . La ventana **módulos** puede indicarle qué módulos trata el depurador como código de usuario, o [*mi código*](../debugger/just-my-code.md), y el estado de carga de símbolos para el módulo. En la mayoría de los escenarios, el depurador busca automáticamente los archivos de símbolos para el código de usuario, pero si desea entrar en el código .NET, el código del sistema o el código de la biblioteca de terceros, o depurarlos, se requieren pasos adicionales para obtener los archivos de símbolos correctos.

![Ver información de símbolos en la ventana módulos](../debugger/media/dbg-tips-modules-window.png "ViewSymbolInformation")

Puede cargar la información de símbolos directamente desde la ventana **módulos** ; para ello, haga clic con el botón secundario y elija **cargar símbolos**.

A veces, los desarrolladores de aplicaciones envían aplicaciones sin los archivos de símbolos coincidentes (para reducir la superficie), pero conservan una copia de los archivos de símbolos coincidentes de la compilación para que puedan depurar una versión de lanzamiento más adelante.

Para averiguar cómo el depurador clasifica el código como código de usuario, vea [solo mi código](../debugger/just-my-code.md). Para obtener más información acerca de los archivos de símbolos, consulte [especificar archivos de código fuente y símbolos (. pdb) en el depurador de Visual Studio](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="learn-more"></a>Más información

Para obtener sugerencias y trucos adicionales e información más detallada, consulte estas entradas de blog:

- [7 hackers menos conocidos para la depuración en Visual Studio](https://devblogs.microsoft.com/visualstudio/7-lesser-known-hacks-for-debugging-in-visual-studio/)
- [7 gemas ocultas en Visual Studio](https://devblogs.microsoft.com/visualstudio/7-hidden-gems-in-visual-studio-2017/)

## <a name="see-also"></a>Vea también

[Métodos abreviados de teclado](../ide/productivity-shortcuts.md)
