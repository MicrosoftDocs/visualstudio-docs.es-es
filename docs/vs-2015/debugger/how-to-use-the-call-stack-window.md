---
title: 'Cómo: usar la ventana pila de llamadas | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.callstack
dev_langs:
- FSharp
- VB
- CSharp
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
caps.latest.revision: 45
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 84c0bfead1633da13b4284cad04ace674045b057
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697485"
---
# <a name="how-to-use-the-call-stack-window"></a>Cómo: Utilizar la ventana Pila de llamadas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mediante la ventana **Pila de llamadas**, puede ver las llamadas a las funciones o procedimientos que están actualmente en la pila.  
  
 La ventana **pila de llamadas** muestra el nombre de cada función y el lenguaje de programación en el que está escrita. El nombre de la función o del procedimiento puede ir acompañado de información opcional, por ejemplo el nombre de módulo, número de línea, así como los nombres, tipos y valores de parámetro. La presentación de esta información opcional se puede activar o desactivar.  
  
 Una flecha amarilla identifica el marco de pila donde está ubicado actualmente el puntero de ejecución. De forma predeterminada, este es el marco cuya información aparece en las ventanas código fuente, **Desensamblado**, **variables locales**, **inspección**y **automático** . Si desea cambiar el contexto a otro marco en la pila, puede hacerlo en la ventana **pila de llamadas** .  
  
 Cuando los símbolos de depuración no están disponibles para parte de una pila de llamadas, la ventana **pila de llamadas** podría no Mostrar información correcta para esa parte de la pila de llamadas. Aparece la notación siguiente:  
  
 [Es posible que lo siguientes marcos no estés o sean incorrectos, no se han cargado símbolos para name.dll]  
  
 En código administrado, de forma predeterminada. la ventana **pila de llamadas** oculta información del código que no es de usuario. Aparece la notación siguiente en lugar de la información oculta:  
  
 **[\<External Code>]**  
  
 El código que no es de usuario es cualquier código que no es de tipo "Mi código". Puede elegir mostrar la información de la pila de llamadas del código que no es de usuario mediante el menú contextual.  
  
 Si utiliza el menú contextual, puede elegir ver las llamadas entre subprocesos.  
  
> [!NOTE]
> Los cuadros de diálogo y los comandos de menú que se ven pueden diferir de los descritos en la Ayuda, dependiendo de los valores de configuración o de edición activos. Para cambiar la configuración, seleccione **Importar y exportar configuraciones** en el menú **Herramientas**. Para obtener más información, consulte [Personalizar la configuración de desarrollo de Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-display-the-call-stack-window-in-break-mode-or-in-run-mode"></a>Para mostrar la ventana Pila de llamadas (en modo de interrupción o en modo de ejecución)  
  
- En el menú **depurar** , seleccione **ventanas** y, a continuación, haga clic en **pila de llamadas**.  
  
### <a name="to-change-the-optional-information-displayed"></a>Para cambiar la información opcional mostrada  
  
- Haga clic con el botón secundario en la ventana **pila de llamadas** y establezca o desactive **Mostrar \<**_the information that you want_**> **.  
  
### <a name="to-display-non-user-code-frames-in-the-call-stack-window"></a>Para mostrar código no definido por usuarios en la ventana Pila de llamadas  
  
- Haga clic con el botón derecho en la ventana **Pila de llamadas** y seleccione **Mostrar código externo**.  
  
### <a name="to-switch-to-another-stack-frame"></a>Para cambiar a otro marco de pila  
  
1. En la ventana **pila de llamadas** , haga clic con el botón secundario en el marco cuyo código y datos desee ver.  
  
2. Seleccione **Cambiar a marco**.  
  
     Una flecha verde con una cola rizada aparece junto al marco que seleccionó. El puntero de ejecución permanece en el marco original, que sigue marcado con la flecha amarilla. Si selecciona **Paso** o **Continuar** en el menú **Depurar**, la ejecución continuará en el marco original, no en el seleccionado.  
  
### <a name="to-display-calls-to-or-from-another-thread"></a>Para mostrar las llamadas a o desde otro subproceso  
  
- Haga clic con el botón derecho en la ventana **Pila de llamadas** y seleccione **Incluir llamadas a otros subprocesos o desde estos**.  
  
### <a name="to-view-the-source-code-for-a-function-on-the-call-stack"></a>Para ver el código fuente de una función de la pila de llamadas  
  
- En la ventana **Pila de llamadas**, haga clic con el botón derecho en la función cuyo código fuente quiera ver y seleccione **Ir a código fuente**.  
  
### <a name="to-visually-trace-the-call-stack"></a>Para hacer un seguimiento visual de la pila de llamadas  
  
1. En la ventana **Pila de llamadas**, abra el menú contextual. Elija **Mostrar pila de llamadas en mapa de código**. (Teclado: **Ctrl**  +  **Shift**  +  **`** )  
  
     Vea [asignar métodos en la pila de llamadas durante la depuración](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
### <a name="to-view-the-disassembly-code-for-a-function-on-the-call-stack"></a>Para ver el código de desensamblado de una función de la pila de llamadas  
  
- En la ventana **Pila de llamadas**, haga clic con el botón derecho en la función cuyo código de desensamblado quiera ver y seleccione **Ir al desensamblado**.  
  
### <a name="to-run-to-a-specific-function-from-the-call-stack-window"></a>Para ejecutar una función concreta desde la ventana Pila de llamadas  
  
- En la ventana **pila de llamadas** , seleccione la función, haga clic con el botón secundario y elija **ejecutar hasta el cursor**.  
  
### <a name="to-set-a-breakpoint-on-the-exit-point-of-a-function-call"></a>Para establecer un punto de interrupción en la salida de una llamada a función  
  
- Vea [Establecer un punto de interrupción en una función de pila de llamadas](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_in_the_call_stack_window).  
  
### <a name="to-load-symbols-for-a-module"></a>Para cargar los símbolos para un módulo  
  
- En la ventana **pila de llamadas** , haga clic con el botón secundario en el marco que muestra el módulo cuyos símbolos desea recargar y seleccione **cargar símbolos**.  
  
## <a name="loading-symbols"></a>Cargar Símbolos  
 En la ventana **Pila de llamadas**, puede cargar los símbolos de depuración para el código que no los tenga cargados. Estos símbolos pueden ser .NET Framework o símbolos del sistema descargados de los servidores de símbolos públicos de Microsoft, o símbolos en una ruta de acceso de símbolos en el equipo que está depurando.  
  
 Consulte [Specify symbol (.pdb) and source files](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) (Especificación de símbolo (.pdb) y archivos de origen).  
  
#### <a name="to-load-symbols"></a>Para cargar símbolos  
  
1. En la ventana **pila de llamadas** , haga clic con el botón secundario en el marco para el que no se cargan los símbolos. Se oscurecerá el marco.  
  
2. Seleccione **cargar símbolos desde** y, a continuación, haga clic en **servidores de símbolos de Microsoft** o ruta de acceso de **símbolos**.  
  
#### <a name="to-set-the-symbol-path"></a>Para configurar la ruta de acceso de símbolos  
  
1. En la ventana **Pila de llamadas**, elija **Configuración de símbolos** en el menú contextual.  
  
     Se abre el cuadro de diálogo **Opciones** y se muestra la página **Símbolos**.  
  
2. Haga clic en **configuración de símbolos**.  
  
3. En el cuadro de diálogo **Opciones**, haga clic en el icono de carpeta.  
  
     En el cuadro **Ubicaciones del archivo de símbolos (.pdb)** , aparece un cursor.  
  
4. Escriba un nombre de la ruta de acceso del directorio a la ubicación de los símbolos en el equipo que está depurando. Para la depuración local, éste es su equipo local. Para la depuración remota, es el equipo remoto.  
  
5. Haga clic en **Aceptar** para cerrar el cuadro de diálogo **Opciones**.  
  
## <a name="see-also"></a>Consulte también  
 [Código mixto e información que falta en la ventana pila de llamadas](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)   
 [Cómo: cambiar el formato numérico de las ventanas del depurador](https://msdn.microsoft.com/library/cd593847-a625-411d-a430-b798346ef18f)   
 [Ver datos en el depurador](../debugger/viewing-data-in-the-debugger.md)   
 [Especificar archivos de código fuente y símbolos (. pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Usar puntos de interrupción](../debugger/using-breakpoints.md)
