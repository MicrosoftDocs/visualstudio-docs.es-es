---
title: Ver la pila de llamadas en el depurador | Microsoft Docs
ms.custom: seodec18
ms.date: 10/29/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.callstack
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
- aspx
helpviewer_keywords:
- threading [Visual Studio], displaying calls to or from
- functions [debugger], viewing code on call stack
- disassembly code
- breakpoints, Call Stack window
- debugging [Visual Studio], switching to another stack frame
- debugging [Visual Studio], Call Stack window
- Call Stack window, viewing source code for functions on the call stack
- stack, switching stack frames
- Call Stack window, viewing disassembly code for functions on the call stack
ms.assetid: 5154a2a1-4729-4dbb-b675-db611a72a731
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 58b8e9bc37cde33a09a06503755f2646cca6f75c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55018805"
---
# <a name="view-the-call-stack-and-use-the-call-stack-window-in-the-debugger"></a>Ver la pila de llamadas y usar la ventana Pila de llamadas en el depurador

Mediante la ventana **Pila de llamadas**, puede ver las llamadas a las funciones o procedimientos que están actualmente en la pila. En la ventana **Pila de llamadas** se muestra el orden en el que se llama a los métodos y las funciones. La pila de llamadas es una buena forma de examinar y entender el flujo de ejecución de una aplicación.

Cuando [símbolos de depuración](#bkmk_symbols) no están disponibles para una parte de una pila de llamadas, el **pila de llamadas** ventana no pueda mostrar información correcta para esa parte de la pila de llamadas, mostrar en su lugar:

`[Frames below may be incorrect and/or missing, no symbols loaded for name.dll]`

> [!NOTE]
> La ventana **Pila de llamadas** es similar a la perspectiva de depuración de algunos IDE, como Eclipse.

> [!NOTE]
> Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos aquí, en función de los valores de configuración o de edición activos. Para cambiar la configuración, seleccione **Importar y exportar configuraciones** en el menú **Herramientas**.  Consulte [Restablecer configuración](../ide/environment-settings.md#reset-settings).

## <a name="view-the-call-stack-while-in-the-debugger"></a>Ver la pila de llamadas en el depurador

- Durante la depuración, en el **depurar** menú, seleccione **Windows > pila de llamadas**.

  ![Ventana Pila de llamadas](../debugger/media/dbg_basics_callstack_window.png "CallStackWindow")

Una flecha amarilla identifica el marco de pila donde está ubicado actualmente el puntero de ejecución. De forma predeterminada, la información de este marco de pila aparece en el origen, **variables locales**, **automático**, **inspección**, y **desensamblado** windows. Para cambiar el contexto del depurador para otro marco en la pila, [cambiar a otro marco de pila](#bkmk_switch).

## <a name="display-non-user-code-in-the-call-stack-window"></a>Mostrar código de no usuario en la ventana Pila de llamadas

-   Haga clic con el botón derecho en la ventana **Pila de llamadas** y seleccione **Mostrar código externo**.

No de usuario es cualquier código que no se muestra cuando [solo mi código](../debugger/just-my-code.md) está habilitado. En código administrado, marcos de código que no es de usuario están ocultos de forma predeterminada. Aparece la notación siguiente en lugar de los marcos de código que no es de usuario:

`[<External Code>]`

## <a name="bkmk_switch"></a> Cambiar a otro marco de pila (cambiar el contexto del depurador)

1.  En el **pila de llamadas** (ventana), con el botón secundario, la pila de marco cuyo código y los datos que desea ver.

    O bien, haga doble clic en un marco en el **pila de llamadas** ventana para cambiar a ese marco.

2.  Seleccione **Cambiar a marco**.

     Una flecha verde con una cola rizada aparece junto al marco de pila que seleccionó. El puntero de ejecución permanece en el marco original, que sigue marcado con la flecha amarilla. Si selecciona **Paso** o **Continuar** en el menú **Depurar**, la ejecución continuará en el marco original, no en el seleccionado.

## <a name="view-the-source-code-for-a-function-on-the-call-stack"></a>Ver el código fuente de una función en la pila de llamadas

-   En la ventana **Pila de llamadas**, haga clic con el botón derecho en la función cuyo código fuente quiera ver y seleccione **Ir a código fuente**.

## <a name="run-to-a-specific-function-from-the-call-stack-window"></a>Ejecutar una función concreta desde la ventana Pila de llamadas

-  En el **pila de llamadas** ventana, seleccione la función, haga clic en y, a continuación, elija **ejecutar hasta el Cursor**.

## <a name="set-a-breakpoint-on-the-exit-point-of-a-function-call"></a>Establecer un punto de interrupción en el punto de salida de una llamada de función

-   Consulte [establecer un punto de interrupción en una función de la pila de llamadas](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_in_the_call_stack_window).

## <a name="display-calls-to-or-from-another-thread"></a>Muestra las llamadas a o desde otro subproceso

-   Haga clic con el botón derecho en la ventana **Pila de llamadas** y seleccione **Incluir llamadas a otros subprocesos o desde estos**.

## <a name="visually-trace-the-call-stack"></a>Realizar un seguimiento la pila de llamadas

En Visual Studio Enterprise (solo), puede ver mapas de código para la pila de llamadas durante la depuración.

- En la ventana **Pila de llamadas**, abra el menú contextual. Elija **Mostrar pila de llamadas en mapa de código** (**Ctrl** + **MAYÚS** + **`**).

    Para obtener más información, consulte [asignar métodos en la pila de llamadas durante la depuración](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

![Mostrar pila de llamadas en mapa de código](../debugger/media/dbg_basics_show_call_stack_on_code_map.gif "ShowCallStackOnCodeMap")

## <a name="view-the-disassembly-code-for-a-function-on-the-call-stack-c-c-visual-basic-f"></a>Ver el código de desensamblado de una función en la pila de llamadas (C#, C++, Visual Basic, F#)

-   En la ventana **Pila de llamadas**, haga clic con el botón derecho en la función cuyo código de desensamblado quiera ver y seleccione **Ir al desensamblado**.

## <a name="change-the-optional-information-displayed"></a>Cambiar la información opcional mostrada

-   Haga clic en el **pila de llamadas** ventana y establezca o desactive **mostrar \<**  _la información que desee_ **>**.

## <a name="bkmk_symbols"></a> Cargar símbolos para un módulo (C#, C++, Visual Basic, F#)

En la ventana **Pila de llamadas**, puede cargar los símbolos de depuración para el código que no los tenga cargados. Estos símbolos pueden ser .NET Framework o símbolos del sistema descargados de los servidores de símbolos públicos de Microsoft, o símbolos en una ruta de acceso de símbolos en el equipo que está depurando.

Consulte [Specify symbol (.pdb) and source files](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) (Especificación de símbolo (.pdb) y archivos de origen).

### <a name="to-load-symbols"></a>Para cargar símbolos

1.  En el **pila de llamadas** (ventana), con el botón secundario, el marco de pila para los símbolos que no se han cargado. Se oscurecerá el marco.

2.  Seleccione **cargar símbolos** y, a continuación, seleccione **servidores de símbolos de Microsoft** (si está disponible), o busque la ruta de acceso de símbolos.

### <a name="to-set-the-symbol-path"></a>Para configurar la ruta de acceso de símbolos

1.  En la ventana **Pila de llamadas**, elija **Configuración de símbolos** en el menú contextual.

     Se abre el cuadro de diálogo **Opciones** y se muestra la página **Símbolos**.

2.  Seleccione **Lores**.

3.  En el cuadro de diálogo **Opciones**, haga clic en el icono de carpeta.

     En el cuadro **Ubicaciones del archivo de símbolos (.pdb)**, aparece un cursor.

4.  Escriba una ruta de acceso de directorio a la posición del símbolo en el equipo que está depurando. Para la depuración local y remota, se trata de una ruta de acceso en el equipo local.

5.  Seleccione **Aceptar** para cerrar el **opciones** cuadro de diálogo.

## <a name="see-also"></a>Vea también

- [Código mixto e información no mostrada en la ventana Pila de llamadas](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)
- [Ver datos en el depurador](../debugger/viewing-data-in-the-debugger.md)
- [Especificación de archivos de código fuente y símbolos (.pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Usar puntos de interrupción](../debugger/using-breakpoints.md)