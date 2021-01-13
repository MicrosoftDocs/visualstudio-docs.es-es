---
title: Depuración de varios procesos | Microsoft Docs
description: Depure de varios procesos en Visual Studio. Inicie procesos y cambie de unos a otros, interrúmpalos, continúe, recorra el código fuente y finalice o desasocie de procesos individuales.
ms.custom: SEO-VS-2020
ms.date: 11/20/2018
ms.topic: how-to
f1_keywords:
- vs.debug.programs
- vs.debug.processes.attaching
- vs.debug.activeprogram
- vs.debug.attaching
- vs.debug.attachedprocesses
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: bde37134-66af-4273-b02e-05b3370c31ab
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 214025c2d128443223594fdb00fcf730e5a8091a
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2020
ms.locfileid: "97728636"
---
# <a name="debug-multiple-processes-c-visual-basic-c"></a>Depuración de varios procesos ( C#, Visual Basic, C++)

Visual Studio puede depurar una solución que tenga varios procesos. Puede iniciar procesos y cambiar de unos a otros, interrumpirlos, continuar y recorrer el código fuente, detener la depuración y finalizar o desasociar de procesos individuales.

## <a name="start-debugging-with-multiple-processes"></a>Iniciar la depuración con varios procesos

Cuando hay más de un proyecto en una solución de Visual Studio que se puede ejecutar de forma independiente, puede seleccionar qué proyecto inicia el depurador. El proyecto de inicio actual aparece en negrita en el **Explorador de soluciones**.

Para cambiar el proyecto de inicio, en el **Explorador de soluciones**, haga clic con el botón derecho en otro proyecto y seleccione **Establecer como proyecto de inicio**.

Para iniciar la depuración de un proyecto desde el **Explorador de soluciones** sin convertirlo en el proyecto de inicio, haga clic con el botón derecho en el proyecto y seleccione **Depurar** > **Iniciar nueva instancia** o **Ir a nueva instancia**.

**Para establecer el proyecto de inicio o varios proyectos a partir de las propiedades de la solución:**

1. Seleccione la solución en el **Explorador de soluciones** y, después, elija el icono **Propiedades** en la barra de herramientas o haga clic con el botón derecho en la solución y seleccione **Propiedades**.

1. En la página **Propiedades**, seleccione **Propiedades comunes** > **Proyecto de inicio**.

   ![Cambiar el tipo de inicio para un proyecto](../debugger/media/dbg_execution_startmultipleprojects.png "DBG_Execution_StartMultipleProjects")

1. Seleccione **Selección actual**, **Proyecto de inicio único** y un archivo de proyecto, o **Proyectos de inicio múltiples**.

   Si selecciona **Proyectos de inicio múltiples**, puede cambiar el orden de inicio y la acción que se realizará para cada proyecto: **Iniciar**, **Iniciar sin depurar** o **Ninguno**.

1. Seleccione **Aplicar** o **Aceptar** para aplicar y cerrar el cuadro de diálogo.

### <a name="attach-to-a-process"></a><a name="BKMK_Attach_to_a_process"></a> Asociar a un proceso

El depurador también se puede *asociar* a las aplicaciones que se ejecutan en procesos fuera de Visual Studio, incluido en dispositivos remotos. Después de asociarse a una aplicación, puede usar el depurador de Visual Studio. Es posible que las características de depuración estén limitadas. Depende de si la aplicación se compiló con información de depuración, si tiene acceso al código fuente de la aplicación y si el compilador JIT está realizando el seguimiento de la información de depuración.

Para más información, vea [Asociar a procesos en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

**Para asociar a un proceso en ejecución:**

1. Con la aplicación en ejecución, seleccione **Depurar** > **Asociar al proceso**.

   ![Cuadro de diálogo Asociar al proceso](../debugger/media/dbg_attachtoprocessdlg.png "Cuadro de diálogo Asociar al proceso")

1. En el cuadro de diálogo **Asociar al proceso**, seleccione el proceso en la lista **Procesos disponibles** y elija **Asociar**.

>[!NOTE]
>El depurador no se asocia automáticamente a un proceso secundario iniciado por un proceso depurado, aunque el proyecto secundario se encuentre en la misma solución. Para depurar un proceso secundario, debe asociar al proceso secundario después de iniciarse, o configurar el editor del Registro de Windows para iniciar el proceso secundario en una nueva instancia del depurador.

### <a name="use-the-registry-editor-to-automatically-start-a-process-in-the-debugger"></a><a name="BKMK_Automatically_start_an_process_in_the_debugger"></a> Usar el editor del Registro para iniciar automáticamente un proceso en el depurador

En ocasiones, es posible que tenga que depurar código de inicio de una aplicación iniciada por otro proceso. Por ejemplo, servicios y configuraciones personalizadas. Puede iniciar el depurador y asociarlo automáticamente a la aplicación.

1. Ejecute *regedit.exe* para iniciar el editor del Registro de Windows.

1. En el editor del Registro, vaya a **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Image File Execution Options**.

1. Seleccione la carpeta de la aplicación que desee iniciar en el depurador.

   Si la aplicación no aparece como una carpeta secundaria, haga clic con el botón derecho en **Image File Execution Options**, seleccione **Nuevo** > **Clave** y escriba el nombre de la aplicación. O bien, haga clic con el botón derecho en la nueva clave en el árbol, elija **Cambiar nombre** y escriba el nombre de la aplicación.

1. Haga clic con el botón derecho en la nueva clave del árbol y elija **Nuevo** > **Valor de cadena**.

1. Cambie el nombre del nuevo valor de **Nuevo valor #1** a `debugger`.

1. Haga clic con el botón derecho en el **depurador** y seleccione **Modificar**.

   ![Cuadro de diálogo Editar cadena](../debugger/media/dbg_execution_automaticstart_editstringdlg.png "Cuadro de diálogo Editar cadena")

1. En el cuadro de diálogo **Editar cadena**, escriba `vsjitdebugger.exe` en el cuadro **Información del valor** y, después, seleccione **Aceptar**.

   ![Entrada de inicio automático del depurador en regedit.exe](../debugger/media/dbg_execution_automaticstart_result.png "Entrada de inicio automático del depurador en regedit.exe")

## <a name="debug-with-multiple-processes"></a><a name="BKMK_Switch_processes__break_and_continue_execution__step_through_source"></a> Depurar con varios procesos
<a name="BKMK_Configure_the_execution_behavior_of_multiple_processes"></a>

Al depurar una aplicación con varios procesos, los comandos del depurador de interrupción, ejecución paso a paso y continuación afectan a todos los procesos de forma predeterminada. Por ejemplo, si un proceso se suspende en un punto de interrupción, también se suspenderá la ejecución de todos los demás procesos. Puede cambiar este comportamiento predeterminado para tener un mejor control sobre los destinos de los comandos de ejecución.

**Para cambiar si se suspenden todos los procesos cuando se interrumpe un proceso:**

- En **Herramientas** (o **Depurar**) > **Opciones** > **Depuración** > **General**, active o desactive la casilla **Interrumpir todos los procesos cuando se interrumpa uno**.

### <a name="break-step-and-continue-commands"></a><a name="BKMK_Break__step__and_continue_commands"></a> Comandos de interrupción, paso y continuación

En esta tabla se describen los comportamientos de los comandos de depuración cuando la casilla **Interrumpir todos los procesos cuando se interrumpa uno** está activada o desactivada:

|**Comando**|Seleccionado|Selección anulada|
|-|-|-|
|**Depurar**  > **Interrumpir todo**|Se interrumpen todos los procesos.|Se interrumpen todos los procesos.|
|**Depurar** > **Continuar**|Se reanudan todos los procesos.|Se reanudan todos los procesos suspendidos.|
|**Depurar** > **Depurar paso a paso por instrucciones**, **Depurar paso a paso por procedimientos** o **Salir de la depuración**|Se ejecutan todos los procesos mientras que el proceso actual se ejecuta paso a paso. <br />A continuación, se interrumpen todos los procesos.|El proceso actual se ejecuta paso a paso. <br />Se reanudan los procesos suspendidos. <br />Continúan los procesos en ejecución.|
|**Depurar** > **Ir al proceso actual**, **Paso a paso por el proceso actual** o **Paso a paso para salir del procedimiento actual**|N/D|El proceso actual se ejecuta paso a paso.<br />Otros procesos mantienen su estado existente (suspendido o en ejecución).|
|Ventana de código fuente **Punto de interrupción**|Se interrumpen todos los procesos.|Solo se interrumpe el proceso de la ventana de código fuente.|
|Ventana de código fuente **Ejecutar hasta el cursor**<br />La ventana de código fuente debe estar en el proceso actual.|Se ejecutan todos los procesos mientras se ejecuta el proceso de la ventana de código fuente hasta el cursor para, a continuación, interrumpirse.<br />A continuación, se interrumpen todos los demás procesos.|El proceso de la ventana de código fuente se ejecuta hasta el cursor.<br />Otros procesos mantienen su estado existente (suspendido o en ejecución).|
|Ventana **Procesos** > **Interrumpir proceso**|N/D|Se interrumpe el proceso seleccionado.<br />Otros procesos mantienen su estado existente (suspendido o en ejecución).|
|Ventana **Procesos** > **Continuar proceso**|N/D|Se reanuda el proceso seleccionado.<br />Otros procesos mantienen su estado existente (suspendido o en ejecución).|

### <a name="find-the-source-and-symbol-pdb-files"></a><a name="BKMK_Find_the_source_and_symbol___pdb__files"></a> Buscar archivos de origen y de símbolos (.pdb)
Para navegar por el código fuente de un proceso, el depurador necesita poder acceder a los archivos de código fuente y los archivos de símbolos. Para obtener más información, vea [Especificar archivos de código fuente y símbolos (.pdb) en el depurador de Visual Studio (C#, C++, Visual Basic, F#)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

Si no puede acceder a los archivos de un proceso, puede navegar a través de la ventana **Desensamblado**. Para obtener más información, vea [Cómo: Uso de la ventana Desensamblado](../debugger/how-to-use-the-disassembly-window.md).

### <a name="switch-between-processes"></a><a name="BKMK_Switch_between_processes"></a> Cambiar entre procesos

Puede asociar a varios procesos mientras realiza la depuración, pero solo un proceso estará activo en el depurador al mismo tiempo. Puede establecer el proceso activo o *actual* en la **Barra de herramientas** de la ubicación de depuración o en la ventana **Procesos**. Para cambiar entre procesos, ambos procesos deben encontrarse en el modo de interrupción.

**Para establecer el proceso actual desde la barra de herramientas Ubicación de depuración:**

1. Para abrir la barra de herramientas **Ubicación de depuración**, seleccione **Ver** > **Barras de herramientas** > **Ubicación de depuración**.

1. Durante la depuración, en la barra de herramientas **Ubicación de depuración**, seleccione el proceso que quiere establecer como el proceso actual en el menú desplegable **Proceso**.

   ![Cambiar entre procesos](../debugger/media/dbg_execution_switchbetweenmodules.png "DBG_Execution_SwitchBetweenModules")

**Para establecer el proceso actual desde la ventana Procesos:**

1. Para abrir la ventana **Procesos**, durante la depuración, seleccione **Depurar** > **Ventanas** > **Procesos**.

1. En la ventana **Procesos**, el proceso actual se marca mediante una flecha amarilla. Haga doble clic en el proceso que quiere establecer como el proceso actual.

   ![Ventana Procesos](../debugger/media/dbg_processeswindow.png "DBG_ProcessesWindow")

Cuando se cambia a un proceso, se establece como el proceso actual para la depuración. Las ventanas del depurador muestran el estado del proceso actual y los comandos de ejecución paso a paso solo afectan al proceso actual.

## <a name="stop-debugging-with-multiple-processes"></a>Detener la depuración con varios procesos

De forma predeterminada, al seleccionar **Depurar** > **Detener depuración**, el depurador finaliza o se desasocia de todos los procesos.

- Si el proceso actual se inició en el depurador, dicho proceso finaliza.

- Si asoció el depurador al proceso actual, el depurador se desasociará del proceso y dejará el proceso en ejecución.

Si inicia la depuración de un proceso desde una solución de Visual Studio, luego asocia a otro proceso que ya se está ejecutando y, después, elige **Detener depuración**, finaliza la sesión de depuración. El proceso que se inició en Visual Studio finaliza, mientras que el proceso que asoció se sigue ejecutando.

Para controlar la manera en que **Detener depuración** afecta a un proceso individual, en la ventana **Procesos**, haga clic con el botón derecho en un proceso y, después, active o desactive la casilla **Desasociar cuando se interrumpa la depuración**.

>[!NOTE]
>La opción **Interrumpir todos los procesos cuando se interrumpa uno** del depurador no afecta a la detención, la finalización o la desasociación de los procesos.

### <a name="stop-terminate-and-detach-commands"></a>Comandos de detención, finalización y desasociación

En esta tabla se describen los comportamientos de los comandos del depurador para detener, finalizar y desasociar con varios procesos:

|**Comando**|**Descripción**|
|-|-|
|**Depurar** > **Detener depuración**|A menos que se cambie el comportamiento en la ventana **Procesos**, se terminan los procesos iniciados por el depurador y se desasocian los procesos asociados.|
|**Depurar** > **Finalizar todo**|Finalizan todos los procesos.|
|**Depurar** > **Desasociar todo**|El depurador se desasocia de todos los procesos.|
|Ventana **Procesos** > **Desasociar proceso**|El depurador se desasocia del proceso seleccionado.<br />Otros procesos mantienen su estado existente (suspendido o en ejecución).|
|Ventana **Procesos** > **Terminar proceso**|Termina el proceso seleccionado.<br />Otros procesos mantienen su estado existente (suspendido o en ejecución).|
|Ventana **Procesos** > **Desasociar cuando se interrumpe la depuración**|Si está seleccionada esta opción, **Depurar** > **Detener depuración** desasocia del proceso seleccionado. <br />Si no está seleccionada, **Depurar** > **Detener depuración** termina el proceso seleccionado. |

## <a name="see-also"></a>Vea también

- [Especificación de archivos de código fuente y símbolos (.pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Asociar a procesos en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Desplazarse por el código con el depurador](../debugger/navigating-through-code-with-the-debugger.md)
- [Depuración Just-In-Time](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Depuración de aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)