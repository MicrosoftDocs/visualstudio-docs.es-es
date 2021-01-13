---
title: 'Preguntas frecuentes: búsqueda de una característica de depuración'
description: Preguntas más frecuentes que le permitirán identificar la característica del depurador que le ayudará a depurar su aplicación.
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
ms.openlocfilehash: a34aa926fca081a498173cd5fcc439a6b3886ba7
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2020
ms.locfileid: "97728036"
---
# <a name="faq---find-the-debugging-feature-you-need-in-visual-studio"></a>Búsqueda de su tarea de depuración en Visual Studio

Use los vínculos incluidos en este artículo si necesita ayuda para asignar su tarea de depuración a la característica correcta del depurador de Visual Studio que sea pertinente. La lista de tareas mostrada aquí engloba tareas comunes, como pausar el código que se va a depurar, inspeccionar variables y enviar mensajes a la ventana **Salida**. Si necesita información general sobre las características del depurador, vea en su lugar [Primer vistazo al depurador](debugger-feature-tour.md).

## <a name="fix-an-exception"></a>Corregir una excepción

- Vea [Corregir una excepción](write-better-code-with-visual-studio.md#fix-an-exception).

## <a name="pause-running-code"></a>Pausar un código en ejecución

- **Pausar un código en ejecución para inspeccionar una línea de código que pueda contener un error**

  Establezca un punto de interrupción. Para más información, vea [Uso de puntos de interrupción](using-breakpoints.md).

- **Pausar e inspeccionar la aplicación cuando alcance un estado específico**

  Pruebe a usar un punto de interrupción condicional para controlar dónde y cuándo se activa un punto de interrupción mediante lógica condicional. Para más información, vea [Condiciones de interrupción](using-breakpoints.md#breakpoint-conditions).

- **Pausar código solo cuando cambie una propiedad o un valor de un objeto específico**

  En C++, establezca un [punto de interrupción de datos](using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus). 
  ::: moniker range=">= vs-2019"
  En las aplicaciones que usan .NET Core 3, también se puede establecer un [punto de interrupción de datos](using-breakpoints.md#BKMK_set_a_data_breakpoint_managed).
  ::: moniker-end

  Si no, solo en C# y F#, se puede [llevar un seguimiento de un identificador de objeto con un punto de interrupción condicional](using-breakpoints.md#using-object-ids-in-breakpoint-conditions-c-and-f).

- **Pausar código dentro de un bucle en una iteración determinada**

  Establezca un punto de interrupción usando **Número de llamadas** como una condición. Para más información, vea [Número de llamadas](using-breakpoints.md#set-a-hit-count-condition).

- **Pausar código al principio de una función cuando se conoce el nombre de la función, pero no su ubicación**

  Esto se puede llevar a cabo con un punto de interrupción de función. Para más información, vea [Establecer puntos de interrupción de función](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file).

- **Pausar código al principio de varias funciones con el mismo nombre**

  Si existen varias funciones con el mismo nombre (funciones sobrecargadas o funciones en proyectos distintos), se puede usar un [punto de interrupción de función](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file).

- **Administrar los puntos de interrupción y llevar un seguimiento**

  Use la ventana **Puntos de interrupción**. Para más información, vea [Administrar puntos de interrupción](using-breakpoints.md#BKMK_Specify_advanced_properties_of_a_breakpoint_).

- **Pausar código y depurar cuando se produzca una excepción controlada o no controlada específica**

  Aunque la aplicación auxiliar de excepciones muestra dónde se ha producido un error, si quiere pausar y depurar el error específico, puede [indicar al depurador que se interrumpa cuando se produzca una excepción](managing-exceptions-with-the-debugger.md#tell-the-debugger-to-break-when-an-exception-is-thrown).

- **Establecer un punto de interrupción en la pila de llamadas**

  Si quiere pausar y depurar código mientras examina el flujo de ejecución o consulta las funciones en las ventanas **Pila de llamadas**, vea [Establecer un punto de interrupción en la ventana Pila de llamadas](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

- **Pausar código en una instrucción de ensamblado específica**

  Para hacerlo, [establezca un punto de interrupción en la ventana Desensamblado](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

## <a name="execute-code"></a>Ejecutar código

- **Comandos para recorrer el código durante la depuración**

  Para más información, vea [Desplazarse por el código con el depurador](navigating-through-code-with-the-debugger.md).

## <a name="inspect-data"></a>Inspeccionar datos

- **Comprobar el valor de las variables durante la ejecución de la aplicación**

  Mantenga el ratón sobre las variables usando la [información sobre datos](view-data-values-in-data-tips-in-the-code-editor.md) o [inspeccione las variables en las ventanas Automático y Variables locales](autos-and-locals-windows.md).

- **Observar el valor cambiante de una variable específica**

  Establezca una inspección de la variable. Para más información, vea [Establecer una inspección de variables](watch-and-quickwatch-windows.md).

- **Ver cadenas demasiado largas para la ventana del depurador**

  Abra el [visualizador de cadenas](view-strings-visualizer.md) integrado durante la depuración.

## <a name="debug-an-app-that-is-already-running"></a>Depurar una aplicación que ya se está ejecutando

- Vea [Adjuntar a un proceso en ejecución](attach-to-running-processes-with-the-visual-studio-debugger.md).

## <a name="debug-multithreaded-applications"></a>Depuración de aplicaciones multiproceso

- Vea [Depurar aplicaciones multiproceso](debug-multithreaded-applications-in-visual-studio.md).

## <a name="configure-debugging"></a>Configuración de depuración

- **Configurar las opciones del depurador**

  Para configurar las opciones del depurador y del proyecto del depurador, vea [Preparación y configuración del depurador](debugger-settings-and-preparation.md).

- **Personalizar la información que se muestra en el depurador**

  Puede que quiera ver información distinta del tipo de objeto como el valor que aparece en las distintas ventanas del depurador. En los códigos de C#, Visual Basic, F# y C++/CLI, use el atributo [DebuggerDisplay](using-the-debuggerdisplay-attribute.md). Respecto a opciones más avanzadas, la interfaz de usuario también se puede personalizar creando un [visualizador personalizado](create-custom-visualizers-of-data.md).

  En el caso de C++ nativo, use el [marco NatVis](create-custom-views-of-native-objects.md).

## <a name="additional-tasks"></a>Tareas adicionales

- **Editar código durante una sesión de depuración**

  Use la opción [Editar y continuar](edit-and-continue.md). En el caso de XAML, use [Recarga activa de XAML](../xaml-tools/xaml-hot-reload.md).

- **Enviar mensajes a la ventana Salida sin modificar código**

  Establezca un punto de seguimiento. Para más información, vea [Uso de puntos de seguimiento](using-tracepoints.md).

- **Ver el orden en el que se llama a las funciones**

  Vea [Cómo ver la pila de llamadas](how-to-use-the-call-stack-window.md).

- **Depurar en equipos remotos**

  Vea [Depuración remota](remote-debugging.md).

- **Corregir problemas de rendimiento**

  Vea [Primer vistazo a la generación de perfiles](../profiling/profiling-feature-tour.md).
