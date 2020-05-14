---
title: Ver la pila de llamadas en el depurador | Microsoft Docs
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
ms.openlocfilehash: 21573f1f8bd49782739027f7dfc2034bb7501a2f
ms.sourcegitcommit: 08c144d290da373df841f04fc799e3133540a541
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/17/2019
ms.locfileid: "72535980"
---
# <a name="view-the-call-stack-and-use-the-call-stack-window-in-the-debugger"></a>Ver la pila de llamadas y usar la ventana pila de llamadas del depurador

Mediante la ventana **Pila de llamadas**, puede ver las llamadas a las funciones o procedimientos que están actualmente en la pila. En la ventana **Pila de llamadas** se muestra el orden en el que se llama a los métodos y las funciones. La pila de llamadas es una buena forma de examinar y entender el flujo de ejecución de una aplicación.

Cuando no haya [símbolos de depuración](#bkmk_symbols) disponibles para una parte de una pila de llamadas, la ventana **Pila de llamadas** podría no mostrar información correcta para esa parte de la pila de llamadas:

`[Frames below may be incorrect and/or missing, no symbols loaded for name.dll]`

> [!NOTE]
> La ventana **Pila de llamadas** es similar a la perspectiva de depuración de algunos IDE, como Eclipse.

> [!NOTE]
> Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos aquí, en función de los valores de configuración o de edición activos. Para cambiar la configuración, seleccione **Importar y exportar configuraciones** en el menú **Herramientas**.  Vea [Restablecer la configuración](../ide/environment-settings.md#reset-settings).

## <a name="view-the-call-stack-while-in-the-debugger"></a>Ver la pila de llamadas mientras está en el depurador

- Durante la depuración, en el menú **Depurar**, seleccione **Ventanas > Pila de llamadas**.

  ![Ventana Pila de llamadas](../debugger/media/dbg_basics_callstack_window.png "CallStackWindow")

Una flecha amarilla identifica el marco de pila donde está ubicado actualmente el puntero de ejecución. De forma predeterminada, la información de este marco de pila aparece en las ventanas del origen **Variables locales**, **Automático**, **Ver** y **Desensamblado**. Para cambiar el contexto del depurador a otro marco en la pila, [cambie a otro marco de pila](#bkmk_switch).

## <a name="display-non-user-code-in-the-call-stack-window"></a>Mostrar código que no es de usuario en la ventana Pila de llamadas

- Haga clic con el botón derecho en la ventana **Pila de llamadas** y seleccione **Mostrar código externo**.

El código que no es de usuario es cualquier código que no se muestra al habilitar [Solo mi código](../debugger/just-my-code.md). En código administrado, los marcos de código que no son de usuario están ocultos de forma predeterminada. Aparece esta notación en lugar de los marcos de código que no es de usuario:

`[<External Code>]`

## <a name="switch-to-another-stack-frame-change-the-debugger-context"></a><a name="bkmk_switch"></a> Cambiar a otro marco de pila (cambiar el contexto del depurador)

1. En la ventana **Pila de llamadas**, haga clic con el botón derecho en el marco cuyo código y datos quiera ver.

    Si lo prefiere, puede hacer doble clic en un marco en la ventana **Pila de llamadas** para cambiar a ese marco.

2. Seleccione **Cambiar a marco**.

     Aparece una flecha verde con una cola rizada junto al marco que seleccionó. El puntero de ejecución permanece en el marco original, que sigue marcado con la flecha amarilla. Si selecciona **Paso** o **Continuar** en el menú **Depurar**, la ejecución continuará en el marco original, no en el seleccionado.

## <a name="view-the-source-code-for-a-function-on-the-call-stack"></a>Ver el código fuente de una función de la pila de llamadas

- En la ventana **Pila de llamadas**, haga clic con el botón derecho en la función cuyo código fuente quiera ver y seleccione **Ir a código fuente**.

## <a name="run-to-a-specific-function-from-the-call-stack-window"></a>Ejecutar una función concreta desde la ventana Pila de llamadas

- En la ventana **Pila de llamadas**, seleccione la función, haga clic con el botón derecho y, después, elija **Ejecutar hasta el cursor**.

## <a name="set-a-breakpoint-on-the-exit-point-of-a-function-call"></a>Establecer un punto de interrupción en el punto de salida de una llamada de función

- Vea [Establecer un punto de interrupción en una función de pila de llamadas](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

## <a name="display-calls-to-or-from-another-thread"></a>Mostrar llamadas a o desde otro subproceso

- Haga clic con el botón derecho en la ventana **Pila de llamadas** y seleccione **Incluir llamadas a otros subprocesos o desde estos**.

## <a name="visually-trace-the-call-stack"></a>Hacer un seguimiento visual de la pila de llamadas

En Visual Studio Enterprise (solo), puede ver los mapas de código de la pila de llamadas durante la depuración.

- En la ventana **Pila de llamadas**, abra el menú contextual. Elija **Mostrar pila de llamadas en mapa de código** (**Ctrl** + **Mayús** +  **`** ).

    Para más información, vea [Asignar métodos en la pila de llamadas durante la depuración](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

![Mostrar pila de llamadas en el mapa de código](../debugger/media/dbg_basics_show_call_stack_on_code_map.gif "ShowCallStackOnCodeMap")

## <a name="view-the-disassembly-code-for-a-function-on-the-call-stack-c-c-visual-basic-f"></a>Ver el código de desensamblado de una función de la pila de llamadas (C#, C++, Visual Basic, F#)

- En la ventana **Pila de llamadas**, haga clic con el botón derecho en la función cuyo código de desensamblado quiera ver y seleccione **Ir al desensamblado**.

## <a name="change-the-optional-information-displayed"></a>Cambiar la información opcional mostrada

- Haga clic con el botón derecho en la ventana **Pila de llamadas** y active o desactive **Mostrar\<** _la información que quiera_ **>** .

## <a name="load-symbols-for-a-module-c-c-visual-basic-f"></a><a name="bkmk_symbols"></a> Cargar símbolos para un módulo (C#, C++, Visual Basic, F#)

En la ventana **Pila de llamadas**, puede cargar los símbolos de depuración para el código que no los tenga cargados. Estos símbolos pueden ser símbolos de .NET o del sistema descargados de los servidores de símbolos públicos de Microsoft, o símbolos en una ruta de acceso de símbolos en el equipo que está depurando.

Consulte [Specify symbol (.pdb) and source files](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) (Especificación de símbolo (.pdb) y archivos de origen).

### <a name="to-load-symbols"></a>Para cargar símbolos

1. En la ventana **Pila de llamadas**, haga clic con el botón derecho en el marco para el cual no están cargados los símbolos. Se oscurecerá el marco.

2. Seleccione **Cargar símbolos** y, después, seleccione **Servidores de símbolos de Microsoft** (si está disponible) o vaya a la ruta de acceso de símbolos.

### <a name="to-set-the-symbol-path"></a>Para configurar la ruta de acceso de símbolos

1. En la ventana **Pila de llamadas**, elija **Configuración de símbolos** en el menú contextual.

     Se abre el cuadro de diálogo **Opciones** y se muestra la página **Símbolos**.

2. Seleccione **Configuración de símbolos**.

3. En el cuadro de diálogo **Opciones**, haga clic en el icono de carpeta.

     En el cuadro **Ubicaciones del archivo de símbolos (.pdb)** , aparece un cursor.

4. Escriba un nombre de la ruta de acceso del directorio a la ubicación de los símbolos en el equipo que está depurando. Para la depuración local y remota, se trata de una ruta de acceso en el equipo local.

5. Seleccione **Aceptar** para cerrar el cuadro de diálogo **Opciones**.

## <a name="see-also"></a>Vea también

- [Código mixto e información no mostrada en la ventana Pila de llamadas](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)
- [Ver datos en el depurador](../debugger/viewing-data-in-the-debugger.md)
- [Especificación de archivos de código fuente y símbolos (.pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Usar puntos de interrupción](../debugger/using-breakpoints.md)