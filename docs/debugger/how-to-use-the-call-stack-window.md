---
title: Ver la pila de llamadas en el depurador de Visual Studio | Documentos de Microsoft
ms.custom: H1Hack27Feb2017
ms.date: 04/06/2017
ms.technology:
- vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a55f940c6310300b458f4497f8659bfc0897d4b7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="view-the-call-stack-and-use-the-call-stack-window-in-the-visual-studio-debugger"></a>Ver la pila de llamadas y usar la ventana Pila de llamadas en el depurador de Visual Studio

Mediante el uso de la **pila de llamadas** ventana, puede ver las llamadas a funciones o procedimientos que están actualmente en la pila. El **pila de llamadas** ventana muestra el orden en el que se esté llamando métodos y funciones. La pila de llamadas es una buena forma de examinar y comprender el flujo de ejecución de una aplicación.
  
Cuando [símbolos de depuración](#bkmk_symbols) no están disponibles para una parte de una pila de llamadas, el **pila de llamadas** ventana posible que no pueda mostrar información correcta para esa parte de la pila de llamadas. Si sucede esto, aparece la notación siguiente:  
  
`[Frames below may be incorrect and/or missing, no symbols loaded for name.dll]`

>  [!NOTE]
> El **pila de llamadas** ventana es similar a la perspectiva de la depuración de algunos IDE como Eclipse. 

> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos aquí, en función de los valores de configuración o de edición activos. Para cambiar la configuración, seleccione **importar y exportar configuraciones** en el **herramientas** menú.  Vea [personalizar el IDE](../ide/personalizing-the-visual-studio-ide.md)
  
## <a name="view-the-call-stack-while-in-the-debugger"></a>Ver la pila de llamadas en el depurador 
  
-   Durante la depuración, en el **depurar** menú, seleccione **Windows > pila de llamadas**.

 ![Ventana Pila de llamadas](../debugger/media/dbg_basics_callstack_window.png "CallStackWindow")

Una flecha amarilla identifica el marco de pila donde está ubicado actualmente el puntero de ejecución. De forma predeterminada, éste es el marco de pila cuya información aparece en el origen, **locales**, **automático**, **inspección**, y **desensamblado** windows . Si desea cambiar el contexto del depurador a otro marco en la pila, puede hacerlo [cambiar a otro marco de pila](#bkmk_switch).   
  
## <a name="display-non-user-code-in-the-call-stack-window"></a>Mostrar código de no usuario en la ventana Pila de llamadas  
  
-   Haga clic en el **pila de llamadas** ventana y seleccione **mostrar código externo**.

No es de usuario es cualquier código que no se muestra cuando [solo mi código](../debugger/just-my-code.md) está habilitado. En código administrado, los marcos del código de usuario no están ocultos de forma predeterminada. Aparece la notación siguiente en lugar de los marcos del código no es de usuario:  
  
**[\<Código externo >]**  
  
## <a name="bkmk_switch"></a> Cambiar a otro marco de pila (cambiar el contexto del depurador)
  
1.  En el **pila de llamadas** (ventana), menú contextual de la pila de marco cuyo código y los datos que desea ver.

    O bien, haga doble clic en un marco en el **pila de llamadas** ventana para cambiar a marco seleccionado. 
  
2.  Seleccione **cambiar a marco**.  
  
     Una flecha verde con una cola rizada aparece junto al marco de pila que seleccionó. El puntero de ejecución permanece en el marco original, que sigue marcado con la flecha amarilla. Si selecciona **paso** o **continuar** desde el **depurar** menú, la ejecución continuará en el marco original, no el marco seleccionado.  
  
## <a name="view-the-source-code-for-a-function-on-the-call-stack"></a>Ver el código fuente de una función en la pila de llamadas  
  
-   En el **pila de llamadas** ventana, haga que la función cuyo código fuente desee ver y seleccione **ir al código fuente**.

## <a name="run-to-a-specific-function-from-the-call-stack-window"></a>Ejecutar una función concreta desde la ventana Pila de llamadas  
  
-  En el **pila de llamadas** ventana, seleccione la función, haga clic en y elija **ejecutar hasta el Cursor**.  
  
## <a name="set-a-breakpoint-on-the-exit-point-of-a-function-call"></a>Establecer un punto de interrupción en el punto de salida de una llamada de función  
  
-   Vea [establecer un punto de interrupción en una función de la pila de llamadas](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_in_the_call_stack_window).

## <a name="display-calls-to-or-from-another-thread"></a>Muestra las llamadas a o desde otro subproceso  
  
-   Haga clic en el **pila de llamadas** ventana y seleccione **incluir llamadas a otros subprocesos**.   
  
## <a name="visually-trace-the-call-stack"></a>Realizar un seguimiento visual la pila de llamadas  

Si usa Visual Studio Enterprise (solo), puede ver mapas de código para la pila de llamadas durante la depuración.

- En el **pila de llamadas** ventana, abra el menú contextual. Elija **Mostrar pila de llamadas en mapa de código**. (Teclado: **CTRL** + **MAYÚS** + **`**)  
  
    Para obtener información detallada, vea [asignar métodos en la pila de llamadas durante la depuración](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

![Mostrar pila de llamadas en mapa de código](../debugger/media/dbg_basics_show_call_stack_on_code_map.gif "ShowCallStackOnCodeMap")
  
## <a name="view-the-disassembly-code-for-a-function-on-the-call-stack"></a>Ver el código de desensamblado de una función en la pila de llamadas  
  
-   En el **pila de llamadas** ventana, haga que la función cuyo código de desensamblado desee ver y seleccione **ir al desensamblado**.    

## <a name="change-the-optional-information-displayed"></a>Cambiar la información opcional mostrada  
  
-   Haga clic en el **pila de llamadas** ventana y Active o desactive **mostrar \< ***la información que desea***>**.  
  
## <a name="bkmk_symbols"></a> Cargar símbolos para un módulo
En el **pila de llamadas** ventana, puede cargar símbolos para el código que no tiene actualmente cargados los símbolos de depuración. Estos símbolos pueden ser .NET Framework o símbolos del sistema descargados de los servidores de símbolos públicos de Microsoft, o símbolos en una ruta de acceso de símbolos en el equipo que está depurando.  
  
Vea [especificar símbolos (.pdb) y archivos de código fuente](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
### <a name="to-load-symbols"></a>Para cargar símbolos  
  
1.  En el **pila de llamadas** (ventana), haga que el marco de pila para los símbolos que no se han cargado. Se oscurecerá el marco.  
  
2.  Seleccione **cargar símbolos** y, a continuación, haga clic en **servidores de símbolos de Microsoft** (si está disponible) o vaya a la ruta de acceso de símbolos.  
  
### <a name="to-set-the-symbol-path"></a>Para configurar la ruta de acceso de símbolos  
  
1.  En el **pila de llamadas** ventana, elija **configuración de símbolos** en el menú contextual.  
  
     El **opciones** abre el cuadro de diálogo y el **símbolos** se muestra la página.  
  
2.  Haga clic en **configuración de símbolos**.  
  
3.  En el **opciones** diálogo cuadro, haga clic en el icono de carpeta.  
  
     En el **ubicaciones del archivo (.pdb) de símbolos** cuadro, aparece un cursor.  
  
4.  Escriba un nombre de la ruta de acceso del directorio a la ubicación de los símbolos en el equipo que está depurando. Para la depuración local y remota, se trata de una ruta de acceso en el equipo local.
  
5.  Haga clic en **Aceptar** para cerrar el cuadro de diálogo **Opciones**.  
  
## <a name="see-also"></a>Vea también  
 [Código mixto e información no mostrada en la ventana Pila de llamadas](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)  
 [Ver los datos en el depurador](../debugger/viewing-data-in-the-debugger.md)   
 [Especificar los símbolos (.pdb) y archivos de código fuente](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Usar puntos de interrupción](../debugger/using-breakpoints.md)