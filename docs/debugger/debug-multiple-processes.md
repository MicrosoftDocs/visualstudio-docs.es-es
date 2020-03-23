---
title: Depurar múltiples procesos ? Microsoft Docs
ms.date: 11/20/2018
ms.topic: conceptual
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
ms.openlocfilehash: 160e219b6fc2ab314f8d0dd91043c18101f2c3a5
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301186"
---
# <a name="debug-multiple-processes-c-visual-basic-c"></a>Depurar varios procesos (C, Visual Basic, C++)

Visual Studio puede depurar una solución que tiene varios procesos. Puede iniciar y cambiar entre procesos, interrumpir, continuar y recorrer paso a paso el origen, detener la depuración y finalizar o desasociarse de procesos individuales.

## <a name="start-debugging-with-multiple-processes"></a>Inicie la depuración con varios procesos

Cuando más de un proyecto de una solución de Visual Studio se puede ejecutar de forma independiente, puede seleccionar qué proyecto inicia el depurador. El proyecto de inicio actual aparece en negrita en el Explorador de **soluciones.**

Para cambiar el proyecto de inicio, en el **Explorador**de soluciones , haga clic con el botón derecho en otro proyecto y seleccione **Establecer como proyecto de inicio**.

Para iniciar la depuración de un proyecto desde el **Explorador** de soluciones sin convertirlo en el proyecto de inicio, haga clic con el botón secundario en el proyecto y seleccione **Depurar iniciar** > **nueva instancia** o Paso a nueva **instancia**.

**Para establecer el proyecto de inicio o varios proyectos desde Propiedades de la solución:**

1. Seleccione la solución en el **Explorador** de soluciones y, a continuación, seleccione el icono **Propiedades** en la barra de herramientas o haga clic con el botón secundario en la solución y seleccione **Propiedades**.

1. En la página **Propiedades** , seleccione Proyecto de**inicio**de **propiedades** > comunes .

   ![Cambiar el tipo de inicio para un proyecto](../debugger/media/dbg_execution_startmultipleprojects.png "DBG_Execution_StartMultipleProjects")

1. Seleccione **Selección actual**, Proyecto de inicio **único** y un archivo de proyecto o Varios proyectos de **inicio**.

   Si selecciona Varios proyectos de **inicio,** puede cambiar el orden de inicio y la acción que se debe realizar para cada proyecto: **Inicio**, **Iniciar sin depurar**o **Ninguno**.

1. Seleccione **Aplicar**o **Aceptar** para aplicar y cerrar el cuadro de diálogo.

### <a name="attach-to-a-process"></a><a name="BKMK_Attach_to_a_process"></a>Adjuntar a un proceso

El depurador también se puede *asociar* a aplicaciones que se ejecutan en procesos fuera de Visual Studio, incluso en dispositivos remotos. Después de adjuntar a una aplicación, puede usar el depurador de Visual Studio. Las características de depuración pueden estar limitadas. Depende de si la aplicación se creó con información de depuración, si tiene acceso al código fuente de la aplicación y si el compilador JIT realiza el seguimiento de la información de depuración.

Para obtener más información, consulte [Adjuntar a procesos en ejecución.](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)

**Para asociar a un proceso en ejecución:**

1. Con la aplicación en ejecución, seleccione **Depurar** > **adjuntar al proceso**.

   ![Adjuntar al cuadro de diálogo Proceso](../debugger/media/dbg_attachtoprocessdlg.png "Cuadro de diálogo Asociar al proceso")

1. En el cuadro de diálogo **Adjuntar al proceso,** seleccione el proceso en la lista **Procesos disponibles** y, a continuación, seleccione **Adjuntar**.

>[!NOTE]
>El depurador no se asocia automáticamente a un proceso secundario iniciado por un proceso depurado, aunque el proyecto secundario se encuentre en la misma solución. Para depurar un proceso secundario, adjunte al proceso secundario después de que se inicie o configure el Editor del Registro de Windows para iniciar el proceso secundario en una nueva instancia del depurador.

### <a name="use-the-registry-editor-to-automatically-start-a-process-in-the-debugger"></a><a name="BKMK_Automatically_start_an_process_in_the_debugger"></a>Utilice el Editor del Registro para iniciar automáticamente un proceso en el depurador

A veces, es posible que deba depurar el código de inicio de una aplicación iniciada por otro proceso. Por ejemplo, servicios y configuraciones personalizadas. Puede hacer que el depurador se inicie y se asocie automáticamente a la aplicación.

1. Inicie el Editor del Registro de Windows ejecutando *regedit.exe*.

1. En el Editor del Registro, desplácese hasta **HKEY_LOCAL_MACHINE, Software, Microsoft, Windows NT, CurrentVersion y Opciones**de ejecución de archivos de imagen .

1. Seleccione la carpeta de la aplicación que desee iniciar en el depurador.

   Si la aplicación no aparece como una carpeta secundaria, haga clic con el botón derecho en Opciones de **ejecución**de archivos de imagen , seleccione **Nueva** > **clave**y escriba el nombre de la aplicación. O bien, haga clic con el botón derecho en la nueva clave del árbol, seleccione **Cambiar nombre**y, a continuación, escriba el nombre de la aplicación.

1. Haga clic con el botón derecho en la nueva clave del árbol y seleccione **Nuevo** > **valor de cadena**.

1. Cambie el nombre del nuevo valor `debugger`de Nuevo valor **#1** a .

1. Haga clic con el **botón derecho** en el depurador y seleccione **Modificar**.

   ![Cuadro de diálogo Editar cadena](../debugger/media/dbg_execution_automaticstart_editstringdlg.png "Cuadro de diálogo Editar cadena")

1. En el cuadro de `vsjitdebugger.exe` diálogo Editar **cadena,** escriba en el cuadro **Datos** de valor y, a continuación, seleccione **Aceptar**.

   ![Entrada de inicio automático del depurador en regedit.exe](../debugger/media/dbg_execution_automaticstart_result.png "Entrada de inicio automático del depurador en regedit.exe")

## <a name="debug-with-multiple-processes"></a><a name="BKMK_Switch_processes__break_and_continue_execution__step_through_source"></a>Depurar con múltiples procesos
<a name="BKMK_Configure_the_execution_behavior_of_multiple_processes"></a>

Al depurar una aplicación con varios procesos, los comandos de interrupción, paso a paso y continuación del depurador afectan a todos los procesos de forma predeterminada. Por ejemplo, cuando un proceso se suspende en un punto de interrupción, también se suspende la ejecución de todos los demás procesos. Puede cambiar este comportamiento predeterminado para tener un mejor control sobre los destinos de los comandos de ejecución.

**Para cambiar si todos los procesos se suspenden cuando se interrumpe un proceso:**

- En **Herramientas** (o **Depurar)**> **Opciones** > **de depuración** > **general**, active o desactive la casilla Interrumpir todos los procesos cuando **se interrumpa un proceso.**

### <a name="break-step-and-continue-commands"></a><a name="BKMK_Break__step__and_continue_commands"></a> Comandos de interrupción, paso y continuación

En la tabla siguiente se describen los comportamientos de los comandos de depuración cuando la casilla **Romper todos los procesos cuando** se interrumpe un proceso está activada o deseleccionada:

|**Comando**|Seleccionado|Selección anulada|
|-|-|-|
|**Depurar**  > **Break All**|Se interrumpen todos los procesos.|Se interrumpen todos los procesos.|
|**Depurar** > **Continuar**|Se reanudan todos los procesos.|Se reanudan todos los procesos suspendidos.|
|**Depurar** > **Paso**a paso , Paso **a paso**o **Salir**|Se ejecutan todos los procesos mientras que el proceso actual se ejecuta paso a paso. <br />A continuación, se interrumpen todos los procesos.|El proceso actual se ejecuta paso a paso. <br />Se reanudan los procesos suspendidos. <br />Continúan los procesos en ejecución.|
|**Depurar** > paso a**proceso actual**, paso a paso sobre proceso **actual**, o salir **proceso actual**|N/D|El proceso actual se ejecuta paso a paso.<br />Otros procesos mantienen su estado existente (suspendido o en ejecución).|
|Ventana de origen **Punto de interrupción**|Se interrumpen todos los procesos.|Solo se interrumpe el proceso de la ventana de código fuente.|
|Ventana de origen **Ejecutar al cursor**<br />La ventana de código fuente debe estar en el proceso actual.|Se ejecutan todos los procesos mientras se ejecuta el proceso de la ventana de código fuente hasta el cursor para, a continuación, interrumpirse.<br />A continuación, se interrumpen todos los demás procesos.|El proceso de la ventana de código fuente se ejecuta hasta el cursor.<br />Otros procesos mantienen su estado existente (suspendido o en ejecución).|
|**Procesa** la ventana > **interrumpir el proceso**|N/D|Se interrumpe el proceso seleccionado.<br />Otros procesos mantienen su estado existente (suspendido o en ejecución).|
|**Ventana Procesos** > **Continuar proceso**|N/D|Se reanuda el proceso seleccionado.<br />Otros procesos mantienen su estado existente (suspendido o en ejecución).|

### <a name="find-the-source-and-symbol-pdb-files"></a><a name="BKMK_Find_the_source_and_symbol___pdb__files"></a> Buscar archivos de origen y de símbolos (.pdb)
Para navegar por el código fuente de un proceso, el depurador necesita acceso a sus archivos de origen y archivos de símbolos. Para obtener más información, vea [Especificar archivos de código fuente y símbolos (.pdb) en el depurador de Visual Studio (C#, C++, Visual Basic, F#)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

Si no puede acceder a los archivos de un proceso, puede navegar mediante la ventana **Desensamblado.** Para obtener más información, consulte [Cómo: Usar la ventana Desensamblado](../debugger/how-to-use-the-disassembly-window.md).

### <a name="switch-between-processes"></a><a name="BKMK_Switch_between_processes"></a> Cambiar entre procesos

Puede asociarse a varios procesos al depurar, pero solo hay un proceso activo en el depurador en un momento dado. Puede establecer el proceso activo o *actual* en la **Barra de herramientas** de la ubicación de depuración o en la ventana **Procesos**. Para cambiar entre procesos, ambos procesos deben encontrarse en el modo de interrupción.

**Para establecer el proceso actual desde la barra de herramientas Ubicación de depuración:**

1. Para abrir la barra de herramientas Ubicación de **depuración,** seleccione **Ver** > ubicación**de depuración**de**barras** > de herramientas .

1. Durante la depuración, en la barra de herramientas Ubicación de **depuración,** seleccione el proceso que desea establecer como proceso actual en la lista desplegable **Proceso.**

   ![Cambiar entre procesos](../debugger/media/dbg_execution_switchbetweenmodules.png "DBG_Execution_SwitchBetweenModules")

**Para configurar el proceso actual desde la ventana Procesos:**

1. Para abrir la ventana **Procesos,** durante la depuración, seleccione **Depurar** > **procesos de****Windows** > .

1. En la ventana **Procesos,** el proceso actual está marcado con una flecha amarilla. Haga doble clic en el proceso que desea establecer como el proceso actual.

   ![Ventana Procesos](../debugger/media/dbg_processeswindow.png "DBG_ProcessesWindow")

Cambiar a un proceso lo establece como el proceso actual con fines de depuración. Las ventanas del depurador muestran el estado del proceso actual y los comandos de paso a paso solo afectan al proceso actual.

## <a name="stop-debugging-with-multiple-processes"></a>Detener la depuración con varios procesos

De forma predeterminada, al seleccionar **Depurar** > **depuración de depuración**, el depurador finaliza o se separa de todos los procesos.

- Si el proceso actual se inició en el depurador, el proceso finaliza.

- Si asoció el depurador al proceso actual, el depurador se desasociará del proceso y dejará el proceso en ejecución.

Si inicia la depuración de un proceso desde una solución de Visual Studio, a continuación, adjuntar a otro proceso que ya se está ejecutando y, a continuación, elija **Detener depuración**, finaliza la sesión de depuración. El proceso que se inició en Visual Studio finaliza, mientras que el proceso al que se asentó sigue ejecutándose.

Para controlar la forma en que **Detener depuración** afecta a un proceso individual, en la ventana **Procesos,** haga clic con el botón derecho en un proceso y, a continuación, active o desactive la casilla **Desasociar al depurar detenida.**

>[!NOTE]
>La opción **Interrumpir todos los procesos cuando un proceso interrumpe el** depurador no afecta a la detención, terminación o desasociación de los procesos.

### <a name="stop-terminate-and-detach-commands"></a>Comandos de detención, finalización y desasociación

En la tabla siguiente se describen los comportamientos de los comandos de detención, terminación y desasociación del depurador con varios procesos:

|**Comando**|**Descripción**|
|-|-|
|**Depurar** > **Detener depuración Depuración**|A menos que se cambie el comportamiento en la ventana **Procesos,** los procesos iniciados por el depurador finalizan y los procesos adjuntos se separan.|
|**Depurar** > **terminar todo**|Todos los procesos han finalizado.|
|**Depurar** > **Separar todo**|El depurador se desasocia de todos los procesos.|
|**Ventana Procesos** > **Separar proceso**|El depurador se desasocia del proceso seleccionado.<br />Otros procesos mantienen su estado existente (suspendido o en ejecución).|
|**Ventana Procesos** > **Terminar proceso**|El proceso seleccionado finaliza.<br />Otros procesos mantienen su estado existente (suspendido o en ejecución).|
|**Procesa** la ventana > **Separar cuando se detiene** la depuración|Si se selecciona, **Depurar** > **Detener depuración depura** se separa del proceso seleccionado. <br />Si no está seleccionado, **Depurar** > **Detener depuración depuración** finaliza el proceso seleccionado. |

## <a name="see-also"></a>Consulte también

- [Especificar archivos de código fuente y símbolos (.pdb) en el depurador de Visual Studio (C#, C++, Visual Basic, F#)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Asociar con procesos en ejecución con el depurador de Visual Studio](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Navegar por el código con el depurador de Visual Studio](../debugger/navigating-through-code-with-the-debugger.md)
- [Deshabilitar al depurador Just-In-Time](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Depurar aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)