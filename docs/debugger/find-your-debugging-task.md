---
title: Búsqueda de la tarea de depuración
description: Identificación de la característica del depurador que le ayudará a depurar la aplicación
ms.custom: ''
ms.date: 10/01/2019
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], find your feature
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 792b5e2d40f7299bf019fd3f9c86697bf008c391
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/25/2020
ms.locfileid: "77578771"
---
# <a name="find-your-debugging-task-in-visual-studio"></a>Buscar la tarea de depuración en Visual Studio

Si necesita ayuda para asignar su tarea de depuración a la característica correcta del depurador de Visual Studio que es relevante, use los vínculos que se proporcionan en este artículo. La lista de tareas aquí incluye tareas comunes, como pausar código para depurar, inspeccionar variables y enviar mensajes a la ventana de **salida** . Si necesita información general sobre las características del depurador, vea [primero examine el depurador](debugger-feature-tour.md) en su lugar.

## <a name="pause-running-code"></a>Pausar el código en ejecución

### <a name="pause-running-code-to-inspect-a-line-of-code-that-may-contain-a-bug"></a>Pausar el código en ejecución para inspeccionar una línea de código que puede contener un error

Establezca un punto de interrupción. Para más información, vea [Uso de puntos de interrupción](using-breakpoints.md).

### <a name="pause-and-inspect-your-app-when-it-reaches-a-specific-state"></a>Pausar e inspeccionar la aplicación cuando alcance un estado específico

Pruebe un punto de interrupción condicional para controlar dónde y cuándo se activa un punto de interrupción mediante la lógica condicional. Para obtener más información, vea [condiciones del punto de interrupción](using-breakpoints.md#breakpoint-conditions).

### <a name="pause-code-only-when-a-specific-objects-property-or-value-changes"></a>Pausar código solo cuando cambia la propiedad o el valor de un objeto concreto

Para C++, establezca un [punto de interrupción de datos](using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus). 
::: moniker range=">= vs-2019"
En el caso de las aplicaciones que usan .NET Core 3, también puede establecer un [punto de interrupción de datos](using-breakpoints.md#BKMK_set_a_data_breakpoint_managed).
::: moniker-end

En caso contrario C# , F# para y solo, puede [realizar el seguimiento de un identificador de objeto con un punto de interrupción condicional](using-breakpoints.md#using-object-ids-in-breakpoint-conditions-c-and-f).

### <a name="pause-code-inside-a-loop-at-a-certain-iteration"></a>Pausar el código dentro de un bucle en una determinada iteración

Establezca un punto de interrupción mediante el **número de llamadas** como una condición. Para obtener más información, consulte [número de llamadas](using-breakpoints.md#set-a-hit-count-condition).

### <a name="pause-code-at-the-start-of-a-function-when-you-know-the-function-name-but-not-its-location"></a>Pausar el código al principio de una función cuando conozca el nombre de la función pero no su ubicación

Puede hacerlo con un punto de interrupción de función. Para obtener más información, vea [establecer puntos de interrupción de función](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file).

### <a name="pause-code-at-the-start-of-multiple-functions-with-the-same-name"></a>Pausar el código al principio de varias funciones con el mismo nombre

Si tiene varias funciones con el mismo nombre (funciones sobrecargadas o funciones en proyectos diferentes), puede usar un punto de [interrupción de función](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file).

### <a name="manage-and-keep-track-of-your-breakpoints"></a>Administrar y realizar un seguimiento de los puntos de interrupción

Use la ventana **puntos de interrupción** . Para obtener más información, vea [administrar puntos de interrupción](using-breakpoints.md#BKMK_Specify_advanced_properties_of_a_breakpoint_).

### <a name="pause-code-and-debug-when-a-specific-handled-or-unhandled-exception-is-thrown"></a>Pausar código y depurar cuando se produce una excepción controlada o no controlada específica

Aunque la aplicación auxiliar de excepciones muestra dónde se produjo un error, si desea pausar y depurar el error específico, puede [indicar al depurador que se interrumpa cuando se produzca una excepción](managing-exceptions-with-the-debugger.md#tell-the-debugger-to-break-when-an-exception-is-thrown).

### <a name="set-a-breakpoint-from-the-call-stack"></a>Establecer un punto de interrupción desde la pila de llamadas

Si desea pausar y depurar el código mientras examina el flujo de ejecución o las funciones de visualización en las ventanas **pila de llamadas** , vea [establecer un punto de interrupción en la ventana pila de llamadas](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

### <a name="pause-code-at-a-specific-assembly-instruction"></a>Pausar código en una instrucción de ensamblado específica

Para ello, [establezca un punto de interrupción en la ventana Desensamblado](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

## <a name="execute-code"></a>Ejecutar código

### <a name="learn-the-commands-to-step-through-your-code-while-debugging"></a>Obtener información sobre los comandos para recorrer el código durante la depuración

Para obtener más información, vea [navegar por el código con el depurador](navigating-through-code-with-the-debugger.md).

## <a name="inspect-data"></a>Inspección de los datos

### <a name="check-the-value-of-variables-while-running-your-app"></a>Comprobar el valor de las variables durante la ejecución de la aplicación

Mantenga el mouse sobre las variables con [sugerencias de datos](view-data-values-in-data-tips-in-the-code-editor.md) o [Inspeccione las variables en la ventana automático y variables locales](autos-and-locals-windows.md).

### <a name="observe-the-changing-value-of-a-specific-variable"></a>Observar el valor cambiante de una variable específica

Establezca un reloj en la variable. Para obtener más información, consulte [set a Watch on variables](watch-and-quickwatch-windows.md).

### <a name="view-strings-that-are-too-long-for-the-debugger-window"></a>Ver cadenas demasiado largas para la ventana del depurador

Abra el [visualizador de cadenas](view-strings-visualizer.md) integrado durante la depuración.

## <a name="configure-debugging"></a>Configuración de depuración

### <a name="customize-information-shown-in-the-debugger"></a>Personalizar la información que se muestra en el depurador

Es posible que desee mostrar información distinta del tipo de objeto como valor en distintas ventanas del depurador. Para C#, Visual Basic, F#y C++/CLI Code, utilice el atributo [DebuggerDisplay](using-the-debuggerdisplay-attribute.md) . Para opciones más avanzadas, también puede personalizar la interfaz de usuario mediante la creación de un [visualizador personalizado](create-custom-visualizers-of-data.md).

En el C++caso de Native, utilice el [marco NatVis](create-custom-views-of-native-objects.md).

### <a name="configure-debugger-settings"></a>Configurar las opciones del depurador

Para configurar las opciones del depurador y la configuración del proyecto del depurador, vea [configuración y preparación](debugger-settings-and-preparation.md)del depurador.

## <a name="additional-tasks"></a>Tareas adicionales

### <a name="fix-an-exception"></a>Corregir una excepción

Consulte [corregir una excepción](write-better-code-with-visual-studio.md#fix-an-exception).

### <a name="edit-code-during-a-debugging-session"></a>Editar código durante una sesión de depuración

Use [Editar y continuar](edit-and-continue.md). Para XAML, use la [recarga activa de XAML](../xaml-tools/xaml-hot-reload.md).

### <a name="send-messages-to-the-output-window-without-modifying-code"></a>Enviar mensajes a la ventana de salida sin modificar el código

Establezca un punto de seguimiento. Para obtener más información, vea [usar puntos de seguimiento](using-tracepoints.md).

## <a name="view-the-order-in-which-functions-are-called"></a>Ver el orden en el que se llama a las funciones

Vea [Cómo ver la pila de llamadas](how-to-use-the-call-stack-window.md).

### <a name="debug-on-remote-machines"></a>Depurar en equipos remotos

Vea [Depuración remota](remote-debugging.md).

### <a name="debug-an-app-that-is-already-running"></a>Depurar una aplicación que ya se está ejecutando

Vea [asociar a un proceso en ejecución](attach-to-running-processes-with-the-visual-studio-debugger.md).

### <a name="debug-multithreaded-applications"></a>Depuración de aplicaciones multiproceso

Consulte [depuración de aplicaciones multiproceso](debug-multithreaded-applications-in-visual-studio.md).

### <a name="fix-performance-issues"></a>Corregir problemas de rendimiento

Vea [el primer vistazo a las herramientas de generación de perfiles](../profiling/profiling-feature-tour.md)