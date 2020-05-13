---
title: Consejos y trucos en el depurador
description: Obtenga información sobre algunas de las características menos conocidas admitidas por el depurador de Visual Studio
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
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301180"
---
# <a name="learn-productivity-tips-and-tricks-for-the-debugger-in-visual-studio"></a>Aprenda consejos y trucos sobre productividad para el depurador en Visual Studio

Lea este tema para obtener información sobre algunos consejos y trucos de productividad para el depurador de Visual Studio. Para obtener un vistazo a las características básicas del depurador, vea [Primero, examine el depurador.](../debugger/debugger-feature-tour.md) En este tema, tratamos algunas áreas que no están incluidas en el recorrido de características.

## <a name="pin-data-tips"></a>Consejos de datos de anclar

Si pasa el cursor con frecuencia sobre las sugerencias de datos durante la depuración, es posible que desee anclar la sugerencia de datos para que la variable se dé acceso rápido. La variable permanece anclada incluso después de reiniciar. Para anclar la sugerencia de datos, haga clic en el icono de pasador mientras pasa el cursor sobre ella. Puede anclar varias variables.

![Anclar una sugerencia de datos](../debugger/media/dbg-tips-data-tips-pinned.png "PinningDataTip")

## <a name="edit-your-code-and-continue-debugging-c-vb-c"></a>Edite el código y continúe con la depuración (C, VB, C++)

En la mayoría de los lenguajes compatibles con Visual Studio, puede editar el código en medio de una sesión de depuración y continuar con la depuración. Para usar esta característica, haga clic en el código con el cursor mientras está en pausa en el depurador, realice las ediciones y presione **F5**, **F10** o **F11** para continuar con la depuración.

![Edición de código y depuración continua](../debugger/media/dbg-tips-edit-and-continue.gif "EditAndContinue")

Para obtener más información sobre el uso de la característica y las limitaciones de esta, consulte [Editar y continuar](../debugger/edit-and-continue.md).

## <a name="edit-xaml-code-and-continue-debugging"></a>Editar código XAML y continuar la depuración

Para modificar el código XAML durante una sesión de depuración, consulte [Escribir y depurar código XAML en ejecución con la recarga frecuente de XAML](../xaml-tools/xaml-hot-reload.md).

## <a name="debug-issues-that-are-hard-to-reproduce"></a>Problemas de depuración que son difíciles de reproducir

Si es difícil o requiere mucho tiempo volver a crear un estado determinado en la aplicación, considere si el uso de un punto de interrupción condicional puede ayudar. Puede usar puntos de [interrupción condicionales](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) y puntos de interrupción de filtro para evitar entrar en el código de la aplicación hasta que la aplicación entre en el estado deseado (por ejemplo, un estado en el que una variable almacena datos incorrectos). Puede establecer condiciones mediante expresiones, filtros, recuentos de aciertos, etc.

#### <a name="to-create-a-conditional-breakpoint"></a>Para crear un punto de interrupción condicional

1. Haga clic con el botón derecho en un icono de punto de interrupción (la bola roja) y elija **Condiciones**.

2. En la ventana **Configuración de punto** de interrupción, escriba una expresión.

    ![Punto de interrupción condicional](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

3. Si está interesado en otro tipo de condición, seleccione **Filtrar** en lugar de **Expresión condicional** en el cuadro de diálogo Configuración de **punto** de interrupción y, a continuación, siga las sugerencias de filtro.

## <a name="configure-the-data-to-show-in-the-debugger"></a>Configure los datos para que se muestren en el depurador

Para C, Visual Basic y C+ (solo código C++/CLI), puede indicar al depurador qué información mostrar mediante el atributo [DebuggerDisplay.](../debugger/using-the-debuggerdisplay-attribute.md) Para el código C++, puede hacer lo mismo utilizando [visualizaciones Natvis](create-custom-views-of-native-objects.md).

## <a name="change-the-execution-flow"></a>Cambio del flujo de ejecución

Con el depurador en pausa en una línea de código, utilice el mouse para agarrar el puntero de flecha amarilla a la izquierda. Mueva el puntero de flecha amarilla a un punto diferente de la ruta de acceso de ejecución de código. A continuación, utilice F5 o un comando step para continuar ejecutando la aplicación.

![Mover el puntero de ejecución](../debugger/media/dbg-tour-move-the-execution-pointer.gif "Mover el puntero de ejecución")

Al cambiar el flujo de ejecución, puede, por ejemplo, comprobar las diferentes rutas de ejecución de código o volver a ejecutar código sin tener que reiniciar el depurador.

> [!WARNING]
> A menudo es necesario tener cuidado con esta característica, ya que puede ser que vea una advertencia en la información en pantalla. También puede ser que reciba otras advertencias. Mover el puntero no puede revertir la aplicación a un estado de aplicación anterior.

## <a name="track-an-out-of-scope-object-c-visual-basic"></a>Realizar un seguimiento de un objeto fuera del ámbito (C, Visual Basic)

Es fácil ver variables mediante ventanas del depurador como la ventana **Inspección.** Sin embargo, cuando una variable sale del ámbito en la ventana **Inspección,** puede observar que está atenuada. En algunos escenarios de aplicación, el valor de una variable puede cambiar incluso cuando la variable está fuera del ámbito y es posible que desee verla de cerca (por ejemplo, una variable puede obtener recolección de elementos no utilizados). Puede realizar un seguimiento de la variable creando un ID de objeto para ella en la ventana **Inspección.**

#### <a name="to-create-an-object-id"></a>Para crear un ID de objeto

1. Establezca un punto de interrupción cerca de una variable de la que desee realizar un seguimiento.

2. Inicie el depurador (**F5**) y deténgase en el punto de interrupción.

3. Busque la variable en la ventana **Locales** (**Depurar > Locales**de > Windows ), haga clic con el botón derecho en la variable y seleccione **Crear ID de objeto**.

    ![Crear un ID de objeto](../debugger/media/dbg-tips-watch-create-object-id.png "CreateObjectID")

4. Debería ver **$** un número más en la ventana **Locales.** Esta variable es el identificador del objeto.

5. Haga clic con el botón derecho en la variable de ID de objeto y elija **Agregar inspección**.

Para obtener más información, consulte [Crear un identificador](../debugger/watch-and-quickwatch-windows.md#bkmk_objectIds)de objeto .

## <a name="view-return-values-for-functions"></a>Ver los valores devueltos para las funciones

Para ver los valores devueltos de las funciones, examine las funciones que aparecen en la ventana **Automático** mientras recorre el código. Para ver el valor devuelto para una función, asegúrese de que la función que le interesa ya se ha ejecutado (presione **F10** una vez si está detenido actualmente en la llamada de función). Si la ventana está cerrada, use **Depurar > Windows > Autos** para abrir la ventana **Autos.**

![Ventana Automático](../debugger/media/dbg-tips-autos-window.png "AutosWindow")

Además, puede introducir funciones en la ventana **Inmediato** para ver los valores devueltos. (Abrirlo con **Depurar > Windows > Inmediato**.)

![Ventana Inmediato](../debugger/media/dbg-tips-immediate-window.png "ImmediateWindow")

También puede utilizar [pseudovariables](../debugger/pseudovariables.md) en la ventana `$ReturnValue` **Inspección** e **Inmediato,** como .

## <a name="inspect-strings-in-a-visualizer"></a><a name="string_visualizer"></a>Inspeccionar cadenas en un visualizador

Cuando se trabaja con cadenas, puede ser útil ver toda la cadena con formato. Para ver una cadena de texto sin formato, XML, HTML o JSON, haga clic en el icono de lupa ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Icono del visualizador") mientras pasa el cursor sobre una variable que contiene un valor de cadena.

![Abra un visualizador de cadenas](../debugger/media/dbg-tips-string-visualizers.png "OpenStringVisualizer")

Un visualizador de cadenas puede ayudarle a averiguar si una cadena tiene un formato incorrecto, dependiendo del tipo de cadena. Por ejemplo, un campo **Value** en blanco indica que el tipo de visualizador no reconoce la cadena. Para obtener más información, vea Cuadro de [diálogo Visualizador](../debugger/string-visualizer-dialog-box.md)de cadenas .

![Visualizador de cadenas JSON](../debugger/media/dbg-tips-string-visualizer-json.png "JSONStringVisualizer")

Para algunos otros tipos, como DataSet y DataTable objetos que aparecen en las ventanas del depurador, también puede abrir un visualizador integrado.

## <a name="break-into-code-on-handled-exceptions"></a>Divida en el código de las excepciones controladas

El depurador irrumpe en el código en las excepciones no controladas. Sin embargo, las excepciones controladas (como las excepciones que se producen dentro de un `try/catch` bloque) también pueden ser un origen de errores y es posible que desee investigar cuándo se producen. Puede configurar el depurador para que se divida en el código de las excepciones controladas también configurando opciones en el cuadro de diálogo Configuración de **excepciones.** Abra este cuadro de diálogo seleccionando Depurar > Configuración de **excepciones de Windows >**.

El cuadro de diálogo Configuración de **excepciones** le permite indicar al depurador que interrumpa el código en excepciones específicas. En la ilustración siguiente, el depurador `System.NullReferenceException` irrumpe en el código cada vez que se produce un. Para obtener más información, consulte [Administración de excepciones](../debugger/managing-exceptions-with-the-debugger.md).

![Cuadro de diálogo Configuración de excepción](../debugger/media/dbg-tips-exception-settings.png "ExceptionSettingsDialogBox")

## <a name="debug-deadlocks-and-race-conditions"></a>Depurar interbloqueos y condiciones de carrera

Si necesita depurar los tipos de problemas que son comunes a las aplicaciones multiproceso, a menudo ayuda a ver la ubicación de los subprocesos durante la depuración. Puede hacerlo fácilmente mediante el botón **Mostrar subprocesos en origen.**

#### <a name="to-show-threads-in-your-source-code"></a>Para mostrar subprocesos en el código fuente

1. Durante la depuración, haga clic en el **botón Mostrar subprocesos en origen** ![Mostrar subprocesos en origen](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker") en la barra de herramientas **Depurar.**

2. Examine el margen interno izquierdo de la ventana. En esta línea, verá un marcador de *subprocesos* Marcador de ![subprocesos](../debugger/media/dbg-thread-marker.png "ThreadMarker") que se asemeja a dos subprocesos de tela. El marcador de subproceso indica que un subproceso se ha detenido en esa ubicación.

    Observe que un marcador de subproceso puede estar parcialmente oculto por un punto de interrupción.

3. Desplace el puntero sobre el marcador de subproceso. Aparece la Información sobre datos. En ella se indican el nombre y el número de id. de subproceso de cada subproceso detenido.

    También puede ver la ubicación de los subprocesos en la [ventana Pilas paralelas](../debugger/get-started-debugging-multithreaded-apps.md).

::: moniker range="vs-2017"
## <a name="examine-payloads-for-web-services-and-network-resources-uwp"></a>Examinar las cargas para los servicios web y los recursos de red (UWP)

En las aplicaciones para UWP, puedes analizar las operaciones de red realizadas con la `Windows.Web.Http` API. Puede utilizar esta herramienta para ayudar a depurar servicios web y recursos de red. Para utilizar la herramienta, seleccione Depurar > Generador de **perfiles**de rendimiento . Seleccione **Red**y, a continuación, elija **Iniciar**. En la aplicación, recorra el escenario que use `Windows.Web.Http` y, después, seleccione **Detener recolección** para generar el informe.

![Herramienta de generación de perfiles de uso de red](../profiling/media/prof-tour-network-usage.png "NetworkUsageProfTool")

Seleccione una operación en la vista de resumen para ver más detalles.

![Información detallada en la herramienta Uso de red](../profiling/media/prof-tour-network-usage-details.png "DetailedViewNetworkUsage")

Para obtener más información, vea [Network Usage](../profiling/network-usage.md) (Uso de red).
::: moniker-end

## <a name="get-more-familiar-with-how-the-debugger-attaches-to-your-app-c-c-visual-basic-f"></a><a name="modules_window"></a>Familiarícese más con la forma en que el depurador se asocia a la aplicación (C, C++, Visual Basic, F))

Para adjuntar a la aplicación en ejecución, el depurador carga archivos de símbolo (.pdb) generados para la misma compilación exacta de la aplicación que está intentando depurar. En algunos escenarios, un poco de conocimiento de los archivos de símbolos puede ser útil. Puede examinar cómo Visual Studio carga archivos de símbolos mediante la ventana **Módulos.**

Abra la ventana **Módulos** durante la depuración seleccionando **Depurar > módulos**de > de Windows . La ventana **Módulos** puede indicarle qué módulos trata el depurador como código de usuario, o [*Mi código*](../debugger/just-my-code.md), y el estado de carga del símbolo para el módulo. En la mayoría de los escenarios, el depurador busca automáticamente archivos de símbolos para el código de usuario, pero si desea entrar (o depurar) código .NET , código del sistema o código de biblioteca de terceros, se requieren pasos adicionales para obtener los archivos de símbolos correctos.

![Ver información de símbolos en la ventana Módulos](../debugger/media/dbg-tips-modules-window.png "ViewSymbolInformation")

Puede cargar información de símbolos directamente desde la ventana **Módulos** haciendo clic con el botón derecho y seleccionando **Cargar símbolos**.

A veces, los desarrolladores de aplicaciones envían aplicaciones sin los archivos de símbolos coincidentes (para reducir el espacio), pero mantienen una copia de los archivos de símbolos coincidentes para la compilación para que puedan depurar una versión publicada más adelante.

Para averiguar cómo el depurador clasifica el código como código de usuario, vea [Solo mi código](../debugger/just-my-code.md). Para obtener más información sobre los archivos de símbolos, vea Especificar archivos de [símbolo (.pdb) y de origen en el depurador](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)de Visual Studio .

## <a name="learn-more"></a>Más información

Para obtener consejos y trucos adicionales e información más detallada, consulta estas entradas de blog:

- [7 hacks menos conocidos para la depuración en Visual Studio](https://devblogs.microsoft.com/visualstudio/7-lesser-known-hacks-for-debugging-in-visual-studio/)
- [7 gemas ocultas en Visual Studio](https://devblogs.microsoft.com/visualstudio/7-hidden-gems-in-visual-studio-2017/)

## <a name="see-also"></a>Consulte también

[Métodos abreviados de teclado](../ide/productivity-shortcuts.md)
