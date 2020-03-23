---
title: Depurar múltiples procesos ? Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.programs
- vs.debug.processes.attaching
- vs.debug.activeprogram
- vs.debug.attaching
- vs.debug.attachedprocesses
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: bde37134-66af-4273-b02e-05b3370c31ab
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9a2679825d41a6360dde05e7511d607f8be69dfa
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301444"
---
# <a name="debug-multiple-processes"></a>Depuración de varios procesos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aquí se indica cómo iniciar procesos de depuración, intercambiar procesos, interrumpir y continuar la ejecución, ejecutar paso a paso el código fuente, detener la depuración y finalizar o desasociar procesos.  
  
## <a name="contents"></a><a name="BKMK_Contents"></a>Contenido  
 [Configurar el comportamiento de ejecución de varios procesos](#BKMK_Configure_the_execution_behavior_of_multiple_processes)  
  
 [Busque los archivos de origen y símbolo (.pdb)](#BKMK_Find_the_source_and_symbol___pdb__files)  
  
 [Empezar varios procesos en una solución de VS, asociar a un proceso, empezar automáticamente un proceso en el depurador](#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 [Cambiar procesos, interrumpir y continuar la ejecución, ejecutar paso a paso el código fuente](#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 [Detener la depuración, terminar o desasociar procesos](#BKMK_Stop_debugging__terminate_or_detach_from_processes)  
  
## <a name="configure-the-execution-behavior-of-multiple-processes"></a><a name="BKMK_Configure_the_execution_behavior_of_multiple_processes"></a>Configurar el comportamiento de ejecución de varios procesos  
 De forma predeterminada, cuando varios procesos se ejecutan en el depurador, los comandos de interrupción, ejecución paso a paso y detención del depurador suelen afectar a todos los procesos. Por ejemplo, si un proceso se suspende en un punto de interrupción, también se suspenderá la ejecución de todos los demás procesos. Puede cambiar este comportamiento predeterminado para tener un mejor control sobre los destinos de los comandos de ejecución.  
  
1. En el menú **Depurar** , elija **Opciones y configuración**.  
  
2. En la página **Depuración**, **General,** desactive la casilla **Romper todos los procesos cuando se interrumpe un proceso.**  
  
   ![Volver a los contenidos](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [superiores](#BKMK_Contents)  
  
## <a name="find-the-source-and-symbol-pdb-files"></a><a name="BKMK_Find_the_source_and_symbol___pdb__files"></a> Buscar archivos de origen y de símbolos (.pdb)  
 Para navegar por el código fuente de un proceso, el depurador necesita acceso a los archivos de código fuente y los archivos de símbolos del proceso. Consulte [Especificar símbolo (.pdb) y Archivos](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)de origen .  
  
 Si no puede tener acceso a los archivos de un proceso, puede navegar utilizando la ventana Desensamblado. Consulte [Cómo: Usar la ventana Desensamblado](../debugger/how-to-use-the-disassembly-window.md)  
  
 ![Volver a los contenidos](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [superiores](#BKMK_Contents)  
  
## <a name="start-multiple-processes-in-a-vs-solution-attach-to-a-process-automatically-start-a-process-in-the-debugger"></a><a name="BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger"></a>Iniciar varios procesos en una solución VS, adjuntar a un proceso, iniciar automáticamente un proceso en el depurador  
  
- [Iniciar la depuración de varios procesos en una solución](#BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution) de Visual Studio • [Cambiar el proyecto](#BKMK_Change_the_startup_project) de inicio • Iniciar un proyecto específico en una [solución](#BKMK_Start_a_specific_project_in_a_solution) • [Iniciar varios proyectos en una solución](#BKMK_Start_multiple_projects_in_a_solution) • [Adjuntar a un proceso](#BKMK_Attach_to_a_process) • Iniciar automáticamente un proceso en [el depurador](#BKMK_Automatically_start_an_process_in_the_debugger)  
  
> [!NOTE]
> El depurador no se asocia automáticamente a un proceso secundario iniciado por un proceso depurado, aunque el proyecto secundario se encuentre en la misma solución. Para depurar un proceso secundario:  
> 
> - Realice la asociación al proceso secundario una vez iniciado.  
> 
>   O bien  
>   - Configure Windows para iniciar automáticamente el proceso secundario en una nueva instancia del depurador.  
  
### <a name="start-debugging-multiple-processes-in-a-visual-studio-solution"></a><a name="BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution"></a>Inicie la depuración de varios procesos en una solución de Visual Studio  
 Si tiene más de un proyecto en una solución de Visual Studio que se puede ejecutar de forma independiente (proyectos que se ejecutan en procesos independientes), puede seleccionar qué proyectos desea que inicie el depurador.  
  
 ![Cambiar el tipo de inicio para un proyecto](../debugger/media/dbg-execution-startmultipleprojects.png "DBG_Execution_StartMultipleProjects")  
  
#### <a name="change-the-startup-project"></a><a name="BKMK_Change_the_startup_project"></a>Cambiar el proyecto de inicio  
 Para cambiar el proyecto de inicio de una solución, seleccione el proyecto en el Explorador de soluciones y, a continuación, elija **Establecer como proyecto** de inicio en el menú contextual.  
  
#### <a name="start-a-specific-project-in-a-solution"></a><a name="BKMK_Start_a_specific_project_in_a_solution"></a>Iniciar un proyecto específico en una solución  
 Para iniciar un proyecto para una solución sin cambiar el proyecto de inicio predeterminado, seleccione el proyecto en el Explorador de soluciones y, a continuación, elija **Depurar** en el menú contextual. A continuación, puede elegir **Start new instance** o Step Into new **instance**.  
  
 ![Volver a la parte superior](../debugger/media/pcs-backtotop.png "PCS_BackToTop") Iniciar varios procesos en una [solución VS, adjuntar a un proceso, iniciar automáticamente un proceso en el depurador](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 ![Volver a los contenidos](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [superiores](#BKMK_Contents)  
  
#### <a name="start-multiple-projects-in-a-solution"></a><a name="BKMK_Start_multiple_projects_in_a_solution"></a>Iniciar varios proyectos en una solución  
  
1. Seleccione la solución en el Explorador de soluciones y, a continuación, elija **Propiedades** en el menú contextual.  
  
2. Seleccione **Propiedades comunes**, Proyecto de **inicio** en el cuadro de diálogo **Propiedades.**  
  
3. Para cada proyecto que desee cambiar, elija Start ( Start ) , **Start without debugging** **(Inicio**) o **None (Ninguno).**  
  
   ![Volver a la parte superior](../debugger/media/pcs-backtotop.png "PCS_BackToTop") Iniciar varios procesos en una [solución VS, adjuntar a un proceso, iniciar automáticamente un proceso en el depurador](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
   ![Volver a los contenidos](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [superiores](#BKMK_Contents)  
  
### <a name="attach-to-a-process"></a><a name="BKMK_Attach_to_a_process"></a>Adjuntar a un proceso  
 El depurador también puede *adjuntar* a programas que se ejecutan en procesos fuera de Visual Studio, incluidos los programas que se ejecutan en un dispositivo remoto. Después de asociar a un programa, podrá usar los comandos de ejecución del depurador, inspeccionar el estado del programa, etc. La capacidad de inspeccionar el programa podría ser limitada, en función de si el programa se ha generado con información de depuración, de si el usuario tiene acceso al código fuente del programa o de si el compilador JIT de Common Language Runtime realiza un seguimiento de la información de depuración.  
  
 Consulte [Adjuntar a procesos en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md) para obtener más información.  
  
 **Asociar a un proceso que se está ejecutando en el equipo local**  
  
 Elija **Depurar**, **Asociar al proceso**. En el cuadro de diálogo **Attach to Process,** seleccione el proceso en la lista **Available Processes** y, a continuación, elija **Attach**.  
  
 ![Adjuntar al cuadro de diálogo Proceso](../debugger/media/dbg-attachtoprocessdlg.png "DBG_AttachToProcessDlg")  
  
 ![Volver a los contenidos](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [superiores](#BKMK_Contents)  
  
### <a name="automatically-start-a-process-in-the-debugger"></a><a name="BKMK_Automatically_start_an_process_in_the_debugger"></a>Iniciar automáticamente un proceso en el depurador  
 En ocasiones, es posible que tenga que depurar código de inicio de un programa iniciado por otro proceso. Por ejemplo, servicios y configuraciones personalizadas. En estos casos, se puede iniciar el depurador y asociarse automáticamente cuando se inicia la aplicación.  
  
1. Inicie el Editor del Registro (**regedit.exe**).  
  
2. Navegue a la carpeta **HKEY_LOCAL_MACHINE, Software, Microsoft, Windows NT, CurrentVersion y Opciones** de ejecución de archivos de imagen.  
  
3. Seleccione la carpeta de la aplicación que desee iniciar en el depurador.  
  
    Si el nombre de la aplicación no aparece como una carpeta secundaria, seleccione Opciones de **ejecución** de archivos de imagen y, a continuación, elija **Nuevo**, **Clave** en el menú contextual. Seleccione la nueva clave, elija **Cambiar nombre** en el menú contextual y, a continuación, escriba el nombre de la aplicación.  
  
4. En el menú contextual de la carpeta de la aplicación, elija **New**, **String Value**.  
  
5. Cambie el nombre del nuevo valor `debugger`de Nuevo **valor** a .  
  
6. En el menú contextual de la entrada del depurador, elija **Modify**.  
  
7. En el cuadro de `vsjitdebugger.exe` diálogo Editar cadena, escriba el cuadro **Datos de valor.**  
  
    ![Cuadro de diálogo Editar cadena](../debugger/media/dbg-execution-automaticstart-editstringdlg.png "DBG_Execution_AutomaticStart_EditStringDlg")  
  
   ![Entrada de inicio automático del depurador en regedit.exe](../debugger/media/dbg-execution-automaticstart-result.png "DBG_Execution_AutomaticStart_Result")  
  
   ![Volver a los contenidos](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [superiores](#BKMK_Contents)  
  
## <a name="switch-processes-break-and-continue-execution-step-through-source"></a><a name="BKMK_Switch_processes__break_and_continue_execution__step_through_source"></a>Cambiar procesos, interrumpir y continuar la ejecución, paso a paso a través de la fuente  
  
- [Cambiar entre procesos](#BKMK_Switch_between_processes) • [Romper, paso y continuar comandos](#BKMK_Break__step__and_continue_commands)  
  
### <a name="switch-between-processes"></a><a name="BKMK_Switch_between_processes"></a> Cambiar entre procesos  
 Puede asociar varios procesos mientras realiza la depuración, pero sólo un proceso estará activo en el depurador al mismo tiempo. Puede establecer el proceso activo o *actual* en la barra de herramientas Ubicación de depuración o en la ventana **Procesos.** Para cambiar entre procesos, ambos procesos deben encontrarse en el modo de interrupción.  
  
 **Para establecer el proceso actual**  
  
- En la barra de herramientas Ubicación de depuración, elija **Procesar** para ver el cuadro de lista **Proceso.** Seleccione el proceso que desee designar como proceso actual.  
  
   ![Cambiar entre procesos](../debugger/media/dbg-execution-switchbetweenmodules.png "DBG_Execution_SwitchBetweenModules")  
  
   Si la barra de herramientas Ubicación de **depuración** no está visible, elija **Herramientas**, **Personalizar**. En la pestaña **Barras de herramientas,** elija **Ubicación de depuración**.  
  
- Abra la ventana **Procesos** (atajo **Ctrl+Alt+Z**), busque el proceso que desea establecer como el proceso actual y haga doble clic en él.  
  
   ![Ventana Procesos](../debugger/media/dbg-processeswindow.png "DBG_ProcessesWindow")  
  
   El proceso actual se marca mediante una flecha amarilla.  
  
  Cuando se cambia a un proyecto, se establece como el proceso actual de la depuración. Cualquier ventana de depurador abierta mostrará el estado del proceso actual, así como todos los comandos de ejecución paso a paso que solo afecten al proceso actual.  
  
  ![Volver a la parte superior](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Cambiar procesos, interrumpir y continuar la ejecución, paso](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source) a través de la fuente  
  
  ![Volver a los contenidos](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [superiores](#BKMK_Contents)  
  
### <a name="break-step-and-continue-commands"></a><a name="BKMK_Break__step__and_continue_commands"></a> Comandos de interrupción, paso y continuación  
  
> [!NOTE]
> De forma predeterminada, los comandos de interrupción, continuación y paso del depurador afectan a todos los procesos que se depuran. Para cambiar este comportamiento, consulte [Configurar el comportamiento de ejecución de varios procesos](#BKMK_Configure_the_execution_behavior_of_multiple_processes)  
  
||||  
|-|-|-|  
|**Comando**|**Romper todos los procesos cuando se rompe un proceso**<br /><br /> Activado (valor predeterminado)|**Romper todos los procesos cuando se rompe un proceso**<br /><br /> Desactivado|  
|**Menú Depurar:**<br /><br /> -   **Break All**|Se interrumpen todos los procesos.|Se interrumpen todos los procesos.|  
|**Menú Depurar:**<br /><br /> -   **Continuar**|Se reanudan todos los procesos.|Se reanudan todos los procesos suspendidos.|  
|**Menú Depurar:**<br /><br /> -   **Paso a paso**<br />-   **Paso más**<br />-   **Step Out**|Se ejecutan todos los procesos mientras que el proceso actual se ejecuta paso a paso.<br /><br /> A continuación, se interrumpen todos los procesos.|El proceso actual se ejecuta paso a paso.<br /><br /> Se reanudan los procesos suspendidos.<br /><br /> Continúan los procesos en ejecución.|  
|**Menú Depurar:**<br /><br /> -   **Paso al proceso actual**<br />-   **Paso sobre el proceso actual**<br />-   **Paso fuera del proceso actual**|N/D|El proceso actual se ejecuta paso a paso.<br /><br /> Otros procesos mantienen su estado existente (suspendido o en ejecución).|  
|Ventana de código fuente<br /><br /> -   **Desempate**|Se interrumpen todos los procesos.|Solo se interrumpe el proceso de la ventana de código fuente.|  
|Menú contextual de la ventana de código fuente:<br /><br /> -   **Ejecutar al cursor**<br /><br /> La ventana de código fuente debe estar en el proceso actual.|Se ejecutan todos los procesos mientras se ejecuta el proceso de la ventana de código fuente hasta el cursor para, a continuación, interrumpirse.<br /><br /> A continuación, se interrumpen todos los demás procesos.|El proceso de la ventana de código fuente se ejecuta hasta el cursor.<br /><br /> Otros procesos mantienen su estado existente (suspendido o en ejecución).|  
|Menú contextual de la ventana **Procesos:**<br /><br /> -   **Proceso de interrupción**|N/D|Se interrumpe el proceso seleccionado.<br /><br /> Otros procesos mantienen su estado existente (suspendido o en ejecución).|  
|Menú contextual de la ventana **Procesos:**<br /><br /> -   **Continuar proceso**|N/D|Se reanuda el proceso seleccionado.<br /><br /> Otros procesos mantienen su estado existente (suspendido o en ejecución).|  
  
 ![Volver a la parte superior](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Cambiar procesos, interrumpir y continuar la ejecución, paso](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source) a través de la fuente  
  
 ![Volver a los contenidos](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [superiores](#BKMK_Contents)  
  
## <a name="stop-debugging-terminate-or-detach-from-processes"></a><a name="BKMK_Stop_debugging__terminate_or_detach_from_processes"></a>Detener la depuración, terminar o separarse de los procesos  
  
- [Comandos de detención, finalización y desasociación](#BKMK_Stop__terminate__and_detach_commands)  
  
  De forma predeterminada, al elegir **Depurar**, **Detener depuración** cuando se abren varios procesos en el depurador, el depurador finaliza o se separa de todos los procesos en función de cómo se abrió el proceso en el depurador:  
  
- Si el proceso actual se inició en el depurador, dicho proceso finalizará.  
  
- Si asoció el depurador al proceso actual, el depurador se desasociará del proceso y dejará el proceso en ejecución.  
  
  Por ejemplo, si inicia la depuración de un proceso desde una solución de Visual Studio, se asocia a otro proceso que ya se está ejecutando y, a continuación, elige **Detener depuración**, finaliza la sesión de depuración, se termina el proceso que se inició en Visual Studio, mientras que el proceso que ha asociado se deja en ejecución. Puede utilizar los siguientes procedimientos para controlar la manera en que se detiene la depuración.  
  
> [!NOTE]
> La opción **Interrumpir todos los procesos cuando se interrumpe un proceso** no afecta a detener la depuración ni a finalizar y separar de los procesos.  
  
 **Para cambiar la manera en que Detener depuración afecta a un proceso individual**  
  
- Abra la ventana **Procesos** (atajo **Ctrl+Alt+Z**). Seleccione un proceso y, a continuación, active o desactive la casilla **Desasociar al depurar se detuvo.**  
  
### <a name="stop-terminate-and-detach-commands"></a><a name="BKMK_Stop__terminate__and_detach_commands"></a>Detener, terminar y separar comandos  
  
|||  
|-|-|  
|**Comando**|**Descripción**|  
|**Menú Depurar:**<br /><br /> -   **Detener depuración**|A menos que la ventana **Procesos** desasocie el comportamiento, la opción **Separar al depurar detiene:**<br /><br /> 1. Los procesos iniciados por el depurador se terminan.<br />2. Los procesos adjuntos se separan del depurador.|  
|**Menú Depurar:**<br /><br /> -   **Terminar todo**|Finalizan todos los procesos.|  
|**Menú Depurar:**<br /><br /> -   **Separar todo**|El depurador se desasocia de todos los procesos.|  
|Menú contextual de la ventana **Procesos:**<br /><br /> -   **Proceso de desasociación**|El depurador se desasocia del proceso seleccionado.<br /><br /> Otros procesos mantienen su estado existente (suspendido o en ejecución).|  
|Menú contextual de la ventana **Procesos:**<br /><br /> -   **Terminar proceso**|Finaliza el proceso seleccionado.<br /><br /> Otros procesos mantienen su estado existente (suspendido o en ejecución).|  
|Menú contextual de la ventana **Procesos:**<br /><br /> -   **Separar cuando se detiene la depuración**|Alterna el comportamiento de **Depurar**, **Detener depuración** para el proceso seleccionado:<br /><br /> - Comprobado: El depurador se separa del proceso.<br />- Borrado: El proceso se termina.|  
  
 ![Volver a la parte superior](../debugger/media/pcs-backtotop.png "PCS_BackToTop") Detener la [depuración, terminar o separar de los procesos](../debugger/debug-multiple-processes.md#BKMK_Stop_debugging__terminate_or_detach_from_processes)  
  
 ![Volver a los contenidos](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [superiores](#BKMK_Contents)  
  
## <a name="see-also"></a>Consulte también  
 [Especificar símbolo (.pdb) y archivos de origen](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Adjuntar a procesos en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Navegar por el código con el depurador](../debugger/navigating-through-code-with-the-debugger.md)   
 [Depuración Just-In-Time](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [Depuración de aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)
