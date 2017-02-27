---
title: "Depurar uno o varios procesos en Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.programs"
  - "vs.debug.processes.attaching"
  - "vs.debug.activeprogram"
  - "vs.debug.attaching"
  - "vs.debug.attachedprocesses"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: bde37134-66af-4273-b02e-05b3370c31ab
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Depurar uno o varios procesos en Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Aquí se indica cómo iniciar procesos de depuración, intercambiar procesos, interrumpir y continuar la ejecución, ejecutar paso a paso el código fuente, detener la depuración y finalizar o desasociar procesos.  
  
##  <a name="BKMK_Contents"></a> Contenido  
 [Configurar el comportamiento de ejecución de varios procesos](#BKMK_Configure_the_execution_behavior_of_multiple_processes)  
  
 [Buscar archivos de origen y de símbolos (.pdb)](#BKMK_Find_the_source_and_symbol___pdb__files)  
  
 [Empezar varios procesos en una solución de VS, asociar a un proceso, empezar automáticamente un proceso en el depurador](#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 [Cambiar procesos, interrumpir y continuar la ejecución, ejecutar paso a paso el código fuente](#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 [Detener la depuración, terminar o desasociar procesos](#BKMK_Stop_debugging__terminate_or_detach_from_processes)  
  
##  <a name="BKMK_Configure_the_execution_behavior_of_multiple_processes"></a> Configurar el comportamiento de ejecución de varios procesos  
 De forma predeterminada, cuando varios procesos se ejecutan en el depurador, los comandos de interrupción, ejecución paso a paso y detención del depurador suelen afectar a todos los procesos.  Por ejemplo, si un proceso se suspende en un punto de interrupción, también se suspenderá la ejecución de todos los demás procesos.  Puede cambiar este comportamiento predeterminado para tener un mejor control sobre los destinos de los comandos de ejecución.  
  
1.  En el menú **Depurar**, elija **Opciones y configuración**.  
  
2.  En la página **Depuración**, **General**, desactive la casilla **Interrumpir todos los procesos cuando se interrumpa uno**.  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Contenido](#BKMK_Contents)  
  
##  <a name="BKMK_Find_the_source_and_symbol___pdb__files"></a> Buscar archivos de origen y de símbolos \(.pdb\)  
 Para navegar por el código fuente de un proceso, el depurador necesita acceso a los archivos de código fuente y los archivos de símbolos del proceso.  Vea [Especificar archivos de código fuente y símbolos \(.pdb\)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
 Si no puede tener acceso a los archivos de un proceso, puede navegar utilizando la ventana Desensamblado.  Vea [Cómo: Utilizar la ventana Desensamblado](../debugger/how-to-use-the-disassembly-window.md).  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Contenido](#BKMK_Contents)  
  
##  <a name="BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger"></a> Empezar varios procesos en una solución de VS, asociar a un proceso, empezar automáticamente un proceso en el depurador  
  
-   [Empezar a depurar varios procesos en una solución de Visual Studio](#BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution) • [Cambiar el proyecto de inicio](#BKMK_Change_the_startup_project) • [Iniciar un proyecto específico en una solución](#BKMK_Start_a_specific_project_in_a_solution) • [Empezar varios proyectos en una solución](#BKMK_Start_multiple_projects_in_a_solution) • [Asociar a un proceso](#BKMK_Attach_to_a_process) • [Iniciar automáticamente un proceso en el depurador](#BKMK_Automatically_start_an_process_in_the_debugger)  
  
> [!NOTE]
>  El depurador no se asocia automáticamente a un proceso secundario iniciado por un proceso depurado, aunque el proyecto secundario se encuentre en la misma solución.  Para depurar un proceso secundario:  
>   
>  -   Realice la asociación al proceso secundario una vez iniciado.  
>   
>      O bien  
> -   Configure Windows para iniciar automáticamente el proceso secundario en una nueva instancia del depurador.  
  
###  <a name="BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution"></a> Empezar a depurar varios procesos en una solución de Visual Studio  
 Si tiene más de un proyecto en una solución de Visual Studio que se puede ejecutar de forma independiente \(proyectos que se ejecutan en procesos independientes\), puede seleccionar qué proyectos desea que inicie el depurador.  
  
 ![Cambiar el tipo de inicio para un proyecto](../debugger/media/dbg_execution_startmultipleprojects.png "DBG\_Execution\_StartMultipleProjects")  
  
####  <a name="BKMK_Change_the_startup_project"></a> Cambiar el proyecto de inicio  
 Para cambiar el proyecto de inicio de una solución, seleccione el proyecto en el Explorador de soluciones y, a continuación, elija **Establecer como proyecto de inicio** en el menú contextual.  
  
####  <a name="BKMK_Start_a_specific_project_in_a_solution"></a> Iniciar un proyecto específico en una solución  
 Para iniciar un proyecto de una solución sin cambiar el proyecto de inicio predeterminado, seleccione el proyecto en el Explorador de soluciones y, a continuación, elija **Depurar** en el menú contextual.  A continuación, puede elegir **Iniciar nueva instancia** o **Ir a nueva instancia**.  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Empezar varios procesos en una solución de VS, asociar a un proceso, empezar automáticamente un proceso en el depurador](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Contenido](#BKMK_Contents)  
  
####  <a name="BKMK_Start_multiple_projects_in_a_solution"></a> Empezar varios proyectos en una solución  
  
1.  Seleccione la solución en el Explorador de soluciones y elija **Propiedades** en el menú contextual.  
  
2.  Seleccione **Propiedades comunes**, **Proyecto de inicio** en el cuadro de diálogo **Propiedades**.  
  
3.  Para cada proyecto que desee cambiar, elija **Inicio**, **Iniciar sin depurar**o **Ninguno**.  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Empezar varios procesos en una solución de VS, asociar a un proceso, empezar automáticamente un proceso en el depurador](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Contenido](#BKMK_Contents)  
  
###  <a name="BKMK_Attach_to_a_process"></a> Asociar a un proceso  
 El depurador también puede *asociarse* a los programas que se ejecutan en procesos externos a Visual Studio, incluidos los programas que se ejecutan en un dispositivo remoto.  Después de asociar a un programa, podrá usar los comandos de ejecución del depurador, inspeccionar el estado del programa, etc.  La capacidad de inspeccionar el programa podría ser limitada, en función de si el programa se ha generado con información de depuración, de si el usuario tiene acceso al código fuente del programa o de si el compilador JIT de Common Language Runtime realiza un seguimiento de la información de depuración.  
  
 Vea [Crear asociaciones con procesos en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md) para obtener más información.  
  
 **Asociar a un proceso que se está ejecutando en el equipo local**  
  
 Elija **Depurar**, **Asociar al proceso**.  En el cuadro de diálogo **Asociar al proceso**, seleccione el proceso en la lista **Procesos disponibles** y elija **Asociar**.  
  
 ![Cuadro de diálogo Asociar al proceso](../debugger/media/dbg_attachtoprocessdlg.png "DBG\_AttachToProcessDlg")  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Contenido](#BKMK_Contents)  
  
###  <a name="BKMK_Automatically_start_an_process_in_the_debugger"></a> Iniciar automáticamente un proceso en el depurador  
 En ocasiones, es posible que tenga que depurar código de inicio de un programa iniciado por otro proceso.  Por ejemplo, servicios y configuraciones personalizadas.  En estos casos, se puede iniciar el depurador y asociarse automáticamente cuando se inicia la aplicación.  
  
1.  Inicie el Editor del Registro \(**regedit.exe**\).  
  
2.  Navegue a la carpeta **HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\Windows NT\\CurrentVersion\\Image File Execution Options**.  
  
3.  Seleccione la carpeta de la aplicación que desee iniciar en el depurador.  
  
     Si el nombre de la aplicación no aparece como carpeta secundaria, seleccione **Image File Execution Options** y, a continuación, elija **Nueva**, **Clave** en el menú contextual.  Seleccione la nueva clave, elija **Cambiar nombre** en el menú contextual y escriba el nombre de la aplicación.  
  
4.  En el menú contextual de la carpeta de aplicaciones, elija **Nuevo**, **Valor de cadena**.  
  
5.  Cambie el nombre del nuevo valor de **New Value** a `depurador`.  
  
6.  En el menú contextual de la entrada del depurador, elija **Modificar**.  
  
7.  En el cuadro de diálogo Editar cadena, escriba `vsjitdebugger.exe` en el cuadro **Datos del valor**.  
  
     ![Cuadro de diálogo Editar cadena](../debugger/media/dbg_execution_automaticstart_editstringdlg.png "DBG\_Execution\_AutomaticStart\_EditStringDlg")  
  
 ![Entrada de inicio automático del depurador en regedit.exe](../debugger/media/dbg_execution_automaticstart_result.png "DBG\_Execution\_AutomaticStart\_Result")  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Contenido](#BKMK_Contents)  
  
##  <a name="BKMK_Switch_processes__break_and_continue_execution__step_through_source"></a> Cambiar procesos, interrumpir y continuar la ejecución, ejecutar paso a paso el código fuente  
  
-   [Cambiar entre procesos](#BKMK_Switch_between_processes) • [Comandos de interrupción, paso y continuación](#BKMK_Break__step__and_continue_commands)  
  
###  <a name="BKMK_Switch_between_processes"></a> Cambiar entre procesos  
 Puede asociar varios procesos mientras realiza la depuración, pero sólo un proceso estará activo en el depurador al mismo tiempo.  Puede establecer el proceso activo o *actual* en la Barra de herramientas de la ubicación de depuración o en la ventana **Procesos**.  Para cambiar entre procesos, ambos procesos deben encontrarse en el modo de interrupción.  
  
 **Para establecer el proceso actual**  
  
-   En la Barra de herramientas de la ubicación de depuración, elija **Proceso** para ver el cuadro de lista **Proceso**.  Seleccione el proceso que desee designar como proceso actual.  
  
     ![Cambiar entre procesos](../debugger/media/dbg_execution_switchbetweenmodules.png "DBG\_Execution\_SwitchBetweenModules")  
  
     Si la barra de herramientas **Ubicación de depuración** no está visible, elija **Herramientas**, **Personalizar**.  En la pestaña **Barras de herramientas**, elija **Ubicación de depuración**.  
  
-   Abra la ventana **Procesos** \(acceso directo: **Ctrl\+Alt\+Z**\), busque el proceso que desea establecer como proceso actual y haga doble clic en él.  
  
     ![Ventana Procesos](../debugger/media/dbg_processeswindow.png "DBG\_ProcessesWindow")  
  
     El proceso actual se marca mediante una flecha amarilla.  
  
 Cuando se cambia a un proyecto, se establece como el proceso actual de la depuración.  Cualquier ventana de depurador abierta mostrará el estado del proceso actual, así como todos los comandos de ejecución paso a paso que solo afecten al proceso actual.  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Cambiar procesos, interrumpir y continuar la ejecución, ejecutar paso a paso el código fuente](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Contenido](#BKMK_Contents)  
  
###  <a name="BKMK_Break__step__and_continue_commands"></a> Comandos de interrupción, paso y continuación  
  
> [!NOTE]
>  De forma predeterminada, los comandos de interrupción, continuación y paso del depurador afectan a todos los procesos que se depuran.  Para cambiar este comportamiento, vea [Configurar el comportamiento de ejecución de varios procesos](#BKMK_Configure_the_execution_behavior_of_multiple_processes)  
  
||||  
|-|-|-|  
|**Comando**|**Interrumpir todos los procesos cuando se interrumpa uno**<br /><br /> Activado \(valor predeterminado\)|**Interrumpir todos los procesos cuando se interrumpa uno**<br /><br /> Borrado|  
|Menú**Depurar**:<br /><br /> -   **Interrumpir todos**|Se interrumpen todos los procesos.|Se interrumpen todos los procesos.|  
|Menú**Depurar**:<br /><br /> -   **Continue**|Se reanudan todos los procesos.|Se reanudan todos los procesos suspendidos.|  
|Menú**Depurar**:<br /><br /> -   **Paso a paso por instrucciones**<br />-   **Paso a paso por procedimientos**<br />-   **Paso a paso para salir**|Se ejecutan todos los procesos mientras que el proceso actual se ejecuta paso a paso.<br /><br /> A continuación, se interrumpen todos los procesos.|El proceso actual se ejecuta paso a paso.<br /><br /> Se reanudan los procesos suspendidos.<br /><br /> Continúan los procesos en ejecución.|  
|Menú**Depurar**:<br /><br /> -   **Ir al proceso actual**<br />-   **Paso a paso por el proceso actual**<br />-   **Paso a paso para salir del procedimiento actual**|N\/D|El proceso actual se ejecuta paso a paso.<br /><br /> Otros procesos mantienen su estado existente \(suspendido o en ejecución\).|  
|Ventana de código fuente<br /><br /> -   **Punto de interrupción**|Se interrumpen todos los procesos.|Solo se interrumpe el proceso de la ventana de código fuente.|  
|Menú contextual de la ventana de código fuente:<br /><br /> -   **Ejecutar hasta el cursor**<br /><br /> La ventana de código fuente debe estar en el proceso actual.|Se ejecutan todos los procesos mientras se ejecuta el proceso de la ventana de código fuente hasta el cursor para, a continuación, interrumpirse.<br /><br /> A continuación, se interrumpen todos los demás procesos.|El proceso de la ventana de código fuente se ejecuta hasta el cursor.<br /><br /> Otros procesos mantienen su estado existente \(suspendido o en ejecución\).|  
|Menú contextual de la ventana**Procesos**:<br /><br /> -   **Interrumpir proceso**|N\/D|Se interrumpe el proceso seleccionado.<br /><br /> Otros procesos mantienen su estado existente \(suspendido o en ejecución\).|  
|Menú contextual de la ventana**Procesos**:<br /><br /> -   **Continuar proceso**|N\/D|Se reanuda el proceso seleccionado.<br /><br /> Otros procesos mantienen su estado existente \(suspendido o en ejecución\).|  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Cambiar procesos, interrumpir y continuar la ejecución, ejecutar paso a paso el código fuente](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Contenido](#BKMK_Contents)  
  
##  <a name="BKMK_Stop_debugging__terminate_or_detach_from_processes"></a> Detener la depuración, terminar o desasociar procesos  
  
-   [Comandos de detención, finalización y desasociación](#BKMK_Stop__terminate__and_detach_commands)  
  
 De forma predeterminada, si elige **Depurar**, **Detener depuración** cuando varios procesos están abiertos en el depurador, este finaliza o se desasocia de todos los procesos según cómo se abriera el proceso en el depurador:  
  
-   Si el proceso actual se inició en el depurador, dicho proceso finalizará.  
  
-   Si asoció el depurador al proceso actual, el depurador se desasociará del proceso y dejará el proceso en ejecución.  
  
 Por ejemplo, si comienza la depuración de un proceso de una solución de Visual Studio, asócielo a otro proceso en ejecución, y después elija **Detener depuración**, la sesión de depuración finaliza, el proceso que se inició en Visual Studio finaliza, mientras el proceso que asoció sigue en ejecución.  Puede utilizar los siguientes procedimientos para controlar la manera en que se detiene la depuración.  
  
> [!NOTE]
>  La opción **Interrumpir todos los procesos cuando se interrumpa uno** no afecta a la detención de la depuración o la finalización o desasociación de los procesos.  
  
 **Para cambiar la manera en que Detener depuración afecta a un proceso individual**  
  
-   Abra la ventana **Procesos** \(acceso directo: **Ctrl\+Alt\+Z**\).  Seleccione un proceso y, a continuación, active o desactive la casilla **Desasociar cuando se interrumpa la depuración**.  
  
###  <a name="BKMK_Stop__terminate__and_detach_commands"></a> Comandos de detención, finalización y desasociación  
  
|||  
|-|-|  
|**Comando**|**Descripción**|  
|Menú**Depurar**:<br /><br /> -   **Detener la depuración**|A menos que se cambie el comportamiento mediante la opción **Desasociar cuando se interrumpa la depuración** de la ventana **Procesos**:<br /><br /> 1.  Finalizan los procesos iniciados por el depurador.<br />2.  Los procesos asociados se desasocian del depurador.|  
|Menú**Depurar**:<br /><br /> -   **Finalizar todo**|Finalizan todos los procesos.|  
|Menú**Depurar**:<br /><br /> -   **Desasociar todo**|El depurador se desasocia de todos los procesos.|  
|Menú contextual de la ventana**Procesos**:<br /><br /> -   **Desasociar proceso**|El depurador se desasocia del proceso seleccionado.<br /><br /> Otros procesos mantienen su estado existente \(suspendido o en ejecución\).|  
|Menú contextual de la ventana**Procesos**:<br /><br /> -   **Terminar proceso**|Finaliza el proceso seleccionado.<br /><br /> Otros procesos mantienen su estado existente \(suspendido o en ejecución\).|  
|Menú contextual de la ventana**Procesos**:<br /><br /> -   **Desasociar cuando se interrumpa la depuración**|Alterna el comportamiento de **Depurar**, **Detener depuración** para el proceso seleccionado:<br /><br /> -   Activado: el depurador se desasocia del proceso.<br />-   Desactivado: finaliza el proceso.|  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Detener la depuración, terminar o desasociar procesos](../debugger/debug-multiple-processes.md#BKMK_Stop_debugging__terminate_or_detach_from_processes)  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Contenido](#BKMK_Contents)  
  
## Vea también  
 [Especificar archivos de código fuente y símbolos \(.pdb\)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Crear asociaciones con procesos en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Desplazarse por el código con el depurador](../debugger/navigating-through-code-with-the-debugger.md)   
 [Depuración Just\-In\-Time](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [Depurar aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)