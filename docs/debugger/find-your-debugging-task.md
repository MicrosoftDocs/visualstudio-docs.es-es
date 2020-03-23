---
title: Búsqueda de la tarea de depuración
description: Identifique la característica del depurador que le ayudará a depurar la aplicación
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
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301150"
---
# <a name="find-your-debugging-task-in-visual-studio"></a>Busque la tarea de depuración en Visual Studio

Si necesita ayuda para asignar la tarea de depuración a la característica correcta del depurador de Visual Studio que es relevante, use los vínculos proporcionados en este artículo. La lista de tareas aquí incluye tareas comunes como pausar código para depurar, inspeccionar variables y enviar mensajes a **la** salida ventana. Si necesita una visión general de las características del depurador, consulte [Primero examine el depurador](debugger-feature-tour.md) en su lugar.

## <a name="pause-running-code"></a>Pausar el código en ejecución

### <a name="pause-running-code-to-inspect-a-line-of-code-that-may-contain-a-bug"></a>Detenga el código en ejecución para inspeccionar una línea de código que puede contener un error

Establezca un punto de interrupción. Para obtener más información, consulte [Uso de puntos](using-breakpoints.md)de interrupción .

### <a name="pause-and-inspect-your-app-when-it-reaches-a-specific-state"></a>Pausa e inspecciona la aplicación cuando alcanza un estado específico

Pruebe un punto de interrupción condicional para controlar dónde y cuándo se activa un punto de interrupción mediante la lógica condicional. Para obtener más información, consulte Condiciones de punto de [interrupción](using-breakpoints.md#breakpoint-conditions).

### <a name="pause-code-only-when-a-specific-objects-property-or-value-changes"></a>Pausar el código solo cuando cambia la propiedad o el valor de un objeto específico

Para C++, establezca un punto de [interrupción](using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus)de datos . 
::: moniker range=">= vs-2019"
Para las aplicaciones que usan .NET Core 3, también puede establecer un punto de interrupción de [datos.](using-breakpoints.md#BKMK_set_a_data_breakpoint_managed)
::: moniker-end

De lo contrario, solo para C- y F, puede realizar un seguimiento de un identificador de objeto con un punto de [interrupción condicional.](using-breakpoints.md#using-object-ids-in-breakpoint-conditions-c-and-f)

### <a name="pause-code-inside-a-loop-at-a-certain-iteration"></a>Pausa el código dentro de un bucle en una cierta iteración

Establezca un punto de interrupción utilizando recuento de **aciertos** como condición. Para obtener más información, consulte [Recuento de aciertos](using-breakpoints.md#set-a-hit-count-condition).

### <a name="pause-code-at-the-start-of-a-function-when-you-know-the-function-name-but-not-its-location"></a>Pausa el código al inicio de una función cuando conozca el nombre de la función, pero no su ubicación

Puede hacerlo con un punto de interrupción de función. Para obtener más información, consulte [Establecer puntos](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file)de interrupción de función .

### <a name="pause-code-at-the-start-of-multiple-functions-with-the-same-name"></a>Pausa el código al inicio de varias funciones con el mismo nombre

Cuando tiene varias funciones con el mismo nombre (funciones o funciones sobrecargadas en diferentes proyectos), puede utilizar un punto de interrupción de [función.](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file)

### <a name="manage-and-keep-track-of-your-breakpoints"></a>Gestione y realice un seguimiento de sus puntos de interrupción

Utilice la ventana **Puntos** de interrupción. Para obtener más información, consulte [Administrar puntos](using-breakpoints.md#BKMK_Specify_advanced_properties_of_a_breakpoint_)de interrupción .

### <a name="pause-code-and-debug-when-a-specific-handled-or-unhandled-exception-is-thrown"></a>Pausar el código y depurar cuando se produce una excepción controlada o no controlada específica

Aunque la aplicación auxiliar de excepciones muestra dónde se produjo un error, si desea pausar y depurar el error específico, puede indicar al depurador que [se interrumpa cuando se produce una excepción.](managing-exceptions-with-the-debugger.md#tell-the-debugger-to-break-when-an-exception-is-thrown)

### <a name="set-a-breakpoint-from-the-call-stack"></a>Establecer un punto de interrupción de la pila de llamadas

Si desea pausar y depurar código mientras examina el flujo de ejecución o ver funciones en **las** ventanas pila de llamadas, consulte Establecer un punto de [interrupción en la ventana Pila](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows)de llamadas .

### <a name="pause-code-at-a-specific-assembly-instruction"></a>Pausar el código en una instrucción de ensamblado específica

Puede hacerlo [estableciendo un punto de interrupción en la ventana Desensamblado](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

## <a name="execute-code"></a>Ejecutar código

### <a name="learn-the-commands-to-step-through-your-code-while-debugging"></a>Aprenda los comandos para recorrer el código mientras se depura

Para obtener más información, vea [Navegar por el código con el depurador.](navigating-through-code-with-the-debugger.md)

## <a name="inspect-data"></a>Inspección de los datos

### <a name="check-the-value-of-variables-while-running-your-app"></a>Compruebe el valor de las variables mientras ejecuta la aplicación

Pase el cursor sobre las variables mediante [sugerencias](view-data-values-in-data-tips-in-the-code-editor.md) de datos o [inspeccione las variables en la ventana Automáticoys y Locales](autos-and-locals-windows.md).

### <a name="observe-the-changing-value-of-a-specific-variable"></a>Observe el valor cambiante de una variable específica

Establezca un reloj en la variable. Para obtener más información, consulte [Establecer un reloj en variables](watch-and-quickwatch-windows.md).

### <a name="view-strings-that-are-too-long-for-the-debugger-window"></a>Ver cadenas que son demasiado largas para la ventana del depurador

Abra el [visualizador](view-strings-visualizer.md) de cadenas integrado durante la depuración.

## <a name="configure-debugging"></a>Configuración de depuración

### <a name="customize-information-shown-in-the-debugger"></a>Personalizar la información que se muestra en el depurador

Es posible que desee mostrar información distinta del tipo de objeto como el valor en diferentes ventanas del depurador. Para el código de C, Visual Basic, F y C++/CLI, use el atributo [DebuggerDisplay.](using-the-debuggerdisplay-attribute.md) Para obtener opciones más avanzadas, también puede personalizar la interfaz de usuario mediante la creación de un [visualizador personalizado.](create-custom-visualizers-of-data.md)

Para C++ nativo, utilice el [marco NatVis](create-custom-views-of-native-objects.md).

### <a name="configure-debugger-settings"></a>Configurar la configuración del depurador

Para configurar las opciones del depurador y la configuración del proyecto del depurador, consulte [Configuración y preparación](debugger-settings-and-preparation.md)del depurador .

## <a name="additional-tasks"></a>Tareas adicionales

### <a name="fix-an-exception"></a>Corregir una excepción

Consulte [Corregir una excepción](write-better-code-with-visual-studio.md#fix-an-exception).

### <a name="edit-code-during-a-debugging-session"></a>Editar código durante una sesión de depuración

Utilice [Editar y continuar](edit-and-continue.md). Para XAML, use [XAML Hot Reload](../xaml-tools/xaml-hot-reload.md).

### <a name="send-messages-to-the-output-window-without-modifying-code"></a>Enviar mensajes a la ventana Salida sin modificar el código

Establezca un punto de seguimiento. Para obtener más información, consulte [Uso de puntos](using-tracepoints.md)de seguimiento .

## <a name="view-the-order-in-which-functions-are-called"></a>Ver el orden en el que se llaman las funciones

Consulte [Cómo ver la pila](how-to-use-the-call-stack-window.md)de llamadas.

### <a name="debug-on-remote-machines"></a>Depurar en máquinas remotas

Vea [Depuración remota](remote-debugging.md).

### <a name="debug-an-app-that-is-already-running"></a>Depurar una aplicación que ya se está ejecutando

Consulte [Adjuntar a procesos en ejecución.](attach-to-running-processes-with-the-visual-studio-debugger.md)

### <a name="debug-multithreaded-applications"></a>Depuración de aplicaciones multiproceso

Consulte [Depurar aplicaciones multiproceso](debug-multithreaded-applications-in-visual-studio.md).

### <a name="fix-performance-issues"></a>Corregir problemas de rendimiento

Consulte Primera mirada a [las herramientas de generación de perfiles](../profiling/profiling-feature-tour.md)