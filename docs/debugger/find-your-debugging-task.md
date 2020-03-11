---
title: Búsqueda de la tarea de depuración
description: Identificación de la característica del depurador que le ayudará a depurar su aplicación.
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
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409226"
---
# <a name="find-your-debugging-task-in-visual-studio"></a>Búsqueda de su tarea de depuración en Visual Studio

Use los vínculos incluidos en este artículo si necesita ayuda para asignar su tarea de depuración a la característica correcta del depurador de Visual Studio que sea pertinente. La lista de tareas mostrada aquí engloba tareas comunes, como pausar el código que se va a depurar, inspeccionar variables y enviar mensajes a la ventana **Salida**. Si necesita información general sobre las características del depurador, vea en su lugar [Primer vistazo al depurador](debugger-feature-tour.md).

## <a name="pause-running-code"></a>Pausar un código en ejecución

### <a name="pause-running-code-to-inspect-a-line-of-code-that-may-contain-a-bug"></a>Pausar un código en ejecución para inspeccionar una línea de código que pueda contener un error

Establezca un punto de interrupción. Para más información, vea [Uso de puntos de interrupción](using-breakpoints.md).

### <a name="pause-and-inspect-your-app-when-it-reaches-a-specific-state"></a>Pausar e inspeccionar la aplicación cuando alcance un estado específico

Pruebe a usar un punto de interrupción condicional para controlar dónde y cuándo se activa un punto de interrupción mediante lógica condicional. Para más información, vea [Condiciones de interrupción](using-breakpoints.md#breakpoint-conditions).

### <a name="pause-code-only-when-a-specific-objects-property-or-value-changes"></a>Pausar código solo cuando cambie una propiedad o un valor de un objeto específico

En C++, establezca un [punto de interrupción de datos](using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus). 
::: moniker range=">= vs-2019"
En las aplicaciones que usan .NET Core 3, también se puede establecer un [punto de interrupción de datos](using-breakpoints.md#BKMK_set_a_data_breakpoint_managed).
::: moniker-end

Si no, solo en C# y F#, se puede [llevar un seguimiento de un identificador de objeto con un punto de interrupción condicional](using-breakpoints.md#using-object-ids-in-breakpoint-conditions-c-and-f).

### <a name="pause-code-inside-a-loop-at-a-certain-iteration"></a>Pausar código dentro de un bucle en una iteración determinada

Establezca un punto de interrupción usando **Número de llamadas** como una condición. Para más información, vea [Número de llamadas](using-breakpoints.md#set-a-hit-count-condition).

### <a name="pause-code-at-the-start-of-a-function-when-you-know-the-function-name-but-not-its-location"></a>Pausar código al principio de una función cuando se conoce el nombre de la función, pero no su ubicación

Esto se puede llevar a cabo con un punto de interrupción de función. Para más información, vea [Establecer puntos de interrupción de función](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file).

### <a name="pause-code-at-the-start-of-multiple-functions-with-the-same-name"></a>Pausar código al principio de varias funciones con el mismo nombre

Si existen varias funciones con el mismo nombre (funciones sobrecargadas o funciones en proyectos distintos), se puede usar un [punto de interrupción de función](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file).

### <a name="manage-and-keep-track-of-your-breakpoints"></a>Administrar los puntos de interrupción y llevar un seguimiento

Use la ventana **Puntos de interrupción**. Para más información, vea [Administrar puntos de interrupción](using-breakpoints.md#BKMK_Specify_advanced_properties_of_a_breakpoint_).

### <a name="pause-code-and-debug-when-a-specific-handled-or-unhandled-exception-is-thrown"></a>Pausar código y depurar cuando se produzca una excepción controlada o no controlada específica

Aunque la aplicación auxiliar de excepciones muestra dónde se ha producido un error, si quiere pausar y depurar el error específico, puede [indicar al depurador que se interrumpa cuando se produzca una excepción](managing-exceptions-with-the-debugger.md#tell-the-debugger-to-break-when-an-exception-is-thrown).

### <a name="set-a-breakpoint-from-the-call-stack"></a>Establecer un punto de interrupción en la pila de llamadas

Si quiere pausar y depurar código mientras examina el flujo de ejecución o consulta las funciones en las ventanas **Pila de llamadas**, vea [Establecer un punto de interrupción en la ventana Pila de llamadas](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

### <a name="pause-code-at-a-specific-assembly-instruction"></a>Pausar código en una instrucción de ensamblado específica

Para hacerlo, [establezca un punto de interrupción en la ventana Desensamblado](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

## <a name="execute-code"></a>Ejecutar código

### <a name="learn-the-commands-to-step-through-your-code-while-debugging"></a>Comandos para recorrer el código durante la depuración

Para más información, vea [Desplazarse por el código con el depurador](navigating-through-code-with-the-debugger.md).

## <a name="inspect-data"></a>Inspeccionar datos

### <a name="check-the-value-of-variables-while-running-your-app"></a>Comprobar el valor de las variables durante la ejecución de la aplicación

Mantenga el ratón sobre las variables usando la [información sobre datos](view-data-values-in-data-tips-in-the-code-editor.md) o [inspeccione las variables en las ventanas Automático y Variables locales](autos-and-locals-windows.md).

### <a name="observe-the-changing-value-of-a-specific-variable"></a>Observar el valor cambiante de una variable específica

Establezca una inspección de la variable. Para más información, vea [Establecer una inspección de variables](watch-and-quickwatch-windows.md).

### <a name="view-strings-that-are-too-long-for-the-debugger-window"></a>Ver cadenas demasiado largas para la ventana del depurador

Abra el [visualizador de cadenas](view-strings-visualizer.md) integrado durante la depuración.

## <a name="configure-debugging"></a>Configuración de depuración

### <a name="customize-information-shown-in-the-debugger"></a>Personalizar la información que se muestra en el depurador

Puede que quiera ver información distinta del tipo de objeto como el valor que aparece en las distintas ventanas del depurador. En los códigos de C#, Visual Basic, F# y C++/CLI, use el atributo [DebuggerDisplay](using-the-debuggerdisplay-attribute.md). Respecto a opciones más avanzadas, la interfaz de usuario también se puede personalizar creando un [visualizador personalizado](create-custom-visualizers-of-data.md).

En el caso de C++ nativo, use el [marco NatVis](create-custom-views-of-native-objects.md).

### <a name="configure-debugger-settings"></a>Configurar las opciones del depurador

Para configurar las opciones del depurador y del proyecto del depurador, vea [Preparación y configuración del depurador](debugger-settings-and-preparation.md).

## <a name="additional-tasks"></a>Tareas adicionales

### <a name="fix-an-exception"></a>Corregir una excepción

Vea [Corregir una excepción](write-better-code-with-visual-studio.md#fix-an-exception).

### <a name="edit-code-during-a-debugging-session"></a>Editar código durante una sesión de depuración

Use la opción [Editar y continuar](edit-and-continue.md). En el caso de XAML, use [Recarga activa de XAML](../xaml-tools/xaml-hot-reload.md).

### <a name="send-messages-to-the-output-window-without-modifying-code"></a>Enviar mensajes a la ventana Salida sin modificar código

Establezca un punto de seguimiento. Para más información, vea [Uso de puntos de seguimiento](using-tracepoints.md).

## <a name="view-the-order-in-which-functions-are-called"></a>Ver el orden en el que se llama a las funciones

Vea [Cómo ver la pila de llamadas](how-to-use-the-call-stack-window.md).

### <a name="debug-on-remote-machines"></a>Depurar en equipos remotos

Vea [Depuración remota](remote-debugging.md).

### <a name="debug-an-app-that-is-already-running"></a>Depurar una aplicación que ya se está ejecutando

Vea [Adjuntar a un proceso en ejecución](attach-to-running-processes-with-the-visual-studio-debugger.md).

### <a name="debug-multithreaded-applications"></a>Depuración de aplicaciones multiproceso

Vea [Depurar aplicaciones multiproceso](debug-multithreaded-applications-in-visual-studio.md).

### <a name="fix-performance-issues"></a>Corregir problemas de rendimiento

Vea [Primer vistazo a la generación de perfiles](../profiling/profiling-feature-tour.md).