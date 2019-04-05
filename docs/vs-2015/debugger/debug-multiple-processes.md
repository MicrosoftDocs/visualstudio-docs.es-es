---
title: Depurar varios procesos | Microsoft Docs
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
ms.openlocfilehash: 1d0986e1780cb9fea061132b5985972cf9635c8b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58986679"
---
# <a name="debug-multiple-processes"></a>Depurar varios procesos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aquí se indica cómo iniciar procesos de depuración, intercambiar procesos, interrumpir y continuar la ejecución, ejecutar paso a paso el código fuente, detener la depuración y finalizar o desasociar procesos.  
  
##  <a name="BKMK_Contents"></a> Contenido  
 [Configurar el comportamiento de ejecución de varios procesos](#BKMK_Configure_the_execution_behavior_of_multiple_processes)  
  
 [Buscar el origen y símbolos (archivos .pdb)](#BKMK_Find_the_source_and_symbol___pdb__files)  
  
 [Empezar varios procesos en una solución de VS, asociar a un proceso, empezar automáticamente un proceso en el depurador](#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 [Cambiar procesos, interrumpir y continuar la ejecución, recorrer el código fuente](#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 [Detener la depuración, terminar o desasociar procesos](#BKMK_Stop_debugging__terminate_or_detach_from_processes)  
  
##  <a name="BKMK_Configure_the_execution_behavior_of_multiple_processes"></a> Configurar el comportamiento de ejecución de varios procesos  
 De forma predeterminada, cuando varios procesos se ejecutan en el depurador, los comandos de interrupción, ejecución paso a paso y detención del depurador suelen afectar a todos los procesos. Por ejemplo, si un proceso se suspende en un punto de interrupción, también se suspenderá la ejecución de todos los demás procesos. Puede cambiar este comportamiento predeterminado para tener un mejor control sobre los destinos de los comandos de ejecución.  
  
1. En el menú **Depurar** , elija **Opciones y configuración**.  
  
2. En el **depuración**, **General** página, desactive la **interrumpir todos los procesos cuando se interrumpa uno** casilla de verificación.  
  
   ![Volver al principio](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contenido](#BKMK_Contents)  
  
##  <a name="BKMK_Find_the_source_and_symbol___pdb__files"></a> Buscar archivos de origen y de símbolos (.pdb)  
 Para navegar por el código fuente de un proceso, el depurador necesita acceso a los archivos de código fuente y los archivos de símbolos del proceso. Consulte [Especificar archivos de código fuente y símbolos (.pdb) en el depurador de Visual Studio](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
 Si no puede tener acceso a los archivos de un proceso, puede navegar utilizando la ventana Desensamblado. Vea [Cómo: Uso de la ventana Desensamblado](../debugger/how-to-use-the-disassembly-window.md)  
  
 ![Volver al principio](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contenido](#BKMK_Contents)  
  
##  <a name="BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger"></a> Empezar varios procesos en una solución de VS, asociar a un proceso, empezar automáticamente un proceso en el depurador  
  
-   [Empezar a depurar varios procesos en una solución de Visual Studio](#BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution) • [cambiar el proyecto de inicio](#BKMK_Change_the_startup_project) • [iniciar un proyecto específico en una solución](#BKMK_Start_a_specific_project_in_a_solution) • [empezar varios proyectos en un solución](#BKMK_Start_multiple_projects_in_a_solution) • [asociar a un proceso](#BKMK_Attach_to_a_process) • [iniciar automáticamente un proceso en el depurador](#BKMK_Automatically_start_an_process_in_the_debugger)  
  
> [!NOTE]
>  El depurador no se asocia automáticamente a un proceso secundario iniciado por un proceso depurado, aunque el proyecto secundario se encuentre en la misma solución. Para depurar un proceso secundario:  
> 
> - Realice la asociación al proceso secundario una vez iniciado.  
> 
>   -o bien-  
>   -   Configure Windows para iniciar automáticamente el proceso secundario en una nueva instancia del depurador.  
  
###  <a name="BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution"></a> Empezar a depurar varios procesos en una solución de Visual Studio  
 Si tiene más de un proyecto en una solución de Visual Studio que se puede ejecutar de forma independiente (proyectos que se ejecutan en procesos independientes), puede seleccionar qué proyectos desea que inicie el depurador.  
  
 ![Cambiar el tipo de inicio para un proyecto](../debugger/media/dbg-execution-startmultipleprojects.png "DBG_Execution_StartMultipleProjects")  
  
####  <a name="BKMK_Change_the_startup_project"></a> Cambiar el proyecto de inicio  
 Para cambiar el proyecto de inicio para una solución, seleccione el proyecto en el Explorador de soluciones y, a continuación, elija **establecer como proyecto de inicio** en el menú contextual.  
  
####  <a name="BKMK_Start_a_specific_project_in_a_solution"></a> Iniciar un proyecto específico en una solución  
 Para iniciar un proyecto de una solución sin cambiar el proyecto de inicio predeterminado, seleccione el proyecto en el Explorador de soluciones y, a continuación, elija **depurar** en el menú contextual. A continuación, puede elegir **Iniciar nueva instancia** o **ir a nueva instancia**.  
  
 ![Volver al principio](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [empezar varios procesos en una solución de VS, asociar a un proceso, empezar automáticamente un proceso en el depurador](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 ![Volver al principio](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contenido](#BKMK_Contents)  
  
####  <a name="BKMK_Start_multiple_projects_in_a_solution"></a> Empezar varios proyectos en una solución  
  
1. Seleccione la solución en el Explorador de soluciones y, a continuación, elija **propiedades** en el menú contextual.  
  
2. Seleccione **propiedades comunes**, **proyecto de inicio** en el **propiedades** cuadro de diálogo.  
  
3. Para cada proyecto que desee cambiar, elija **iniciar**, **iniciar sin depurar**, o **ninguno**.  
  
   ![Volver al principio](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [empezar varios procesos en una solución de VS, asociar a un proceso, empezar automáticamente un proceso en el depurador](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
   ![Volver al principio](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contenido](#BKMK_Contents)  
  
###  <a name="BKMK_Attach_to_a_process"></a> Asociar a un proceso  
 El depurador también puede *adjuntar* a los programas que se ejecutan en procesos fuera de Visual Studio, incluidos los programas que se ejecutan en un dispositivo remoto. Después de asociar a un programa, podrá usar los comandos de ejecución del depurador, inspeccionar el estado del programa, etc. La capacidad de inspeccionar el programa podría ser limitada, en función de si el programa se ha generado con información de depuración, de si el usuario tiene acceso al código fuente del programa o de si el compilador JIT de Common Language Runtime realiza un seguimiento de la información de depuración.  
  
 Consulte [adjuntar a procesos en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md) para obtener más información.  
  
 **Asociar a un proceso que se está ejecutando en el equipo local**  
  
 Elija **depurar**, **asociar al proceso**. En el **asociar al proceso** cuadro de diálogo, seleccione el proceso desde el **procesos disponibles** lista y, a continuación, elija **adjuntar**.  
  
 ![Adjuntar al cuadro de diálogo procesar](../debugger/media/dbg-attachtoprocessdlg.png "DBG_AttachToProcessDlg")  
  
 ![Volver al principio](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contenido](#BKMK_Contents)  
  
###  <a name="BKMK_Automatically_start_an_process_in_the_debugger"></a> Iniciar automáticamente un proceso en el depurador  
 En ocasiones, es posible que tenga que depurar código de inicio de un programa iniciado por otro proceso. Por ejemplo, servicios y configuraciones personalizadas. En estos casos, se puede iniciar el depurador y asociarse automáticamente cuando se inicia la aplicación.  
  
1. Inicie el Editor del registro (**regedit.exe**).  
  
2. Navegue hasta la **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Image File Execution Options** carpeta.  
  
3. Seleccione la carpeta de la aplicación que desee iniciar en el depurador.  
  
    Si el nombre de la aplicación no aparece como una carpeta secundaria, seleccione **Image File Execution Options** y, a continuación, elija **New**, **clave** en el menú contextual. Seleccione la nueva clave, elija **cambiar el nombre** en el menú contextual y, a continuación, escriba el nombre de la aplicación.  
  
4. En el menú contextual de la carpeta de la aplicación, elija **New**, **valor de cadena**.  
  
5. Cambiar el nombre del nuevo valor de **nuevo valor** a `debugger`.  
  
6. En el menú contextual de la entrada del depurador, elija **modificar**.  
  
7. En el cuadro de diálogo Editar cadena, escriba `vsjitdebugger.exe` en el **datos del valor** cuadro.  
  
    ![Editar cuadro de diálogo cadena](../debugger/media/dbg-execution-automaticstart-editstringdlg.png "DBG_Execution_AutomaticStart_EditStringDlg")  
  
   ![Entrada de inicio automático del depurador en regedit.exe](../debugger/media/dbg-execution-automaticstart-result.png "DBG_Execution_AutomaticStart_Result")  
  
   ![Volver al principio](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contenido](#BKMK_Contents)  
  
##  <a name="BKMK_Switch_processes__break_and_continue_execution__step_through_source"></a> Cambiar procesos, interrumpir y continuar la ejecución, recorrer el código fuente  
  
-   [Cambiar entre procesos](#BKMK_Switch_between_processes) • [interrupción, paso y continuar de comandos](#BKMK_Break__step__and_continue_commands)  
  
###  <a name="BKMK_Switch_between_processes"></a> Cambiar entre procesos  
 Puede asociar varios procesos mientras realiza la depuración, pero sólo un proceso estará activo en el depurador al mismo tiempo. Puede establecer el activo o *actual* procesos en la barra de herramientas ubicación de depuración o en el **procesos** ventana. Para cambiar entre procesos, ambos procesos deben encontrarse en el modo de interrupción.  
  
 **Para establecer el proceso actual**  
  
- En la barra de herramientas ubicación de depuración, elija **proceso** para ver el **proceso** cuadro de lista. Seleccione el proceso que desee designar como proceso actual.  
  
   ![Cambiar entre procesos](../debugger/media/dbg-execution-switchbetweenmodules.png "DBG_Execution_SwitchBetweenModules")  
  
   Si el **ubicación de depuración** no está visible la barra de herramientas, elija **herramientas**, **personalizar**. En el **las barras de herramientas** ficha, elija **ubicación de depuración**.  
  
- Abra el **procesos** ventana (método abreviado **Ctrl + Alt + Z**), busque el proceso que desea establecer como proceso actual y haga doble clic en él.  
  
   ![Ventana procesos](../debugger/media/dbg-processeswindow.png "DBG_ProcessesWindow")  
  
   El proceso actual se marca mediante una flecha amarilla.  
  
  Cuando se cambia a un proyecto, se establece como el proceso actual de la depuración. Cualquier ventana de depurador abierta mostrará el estado del proceso actual, así como todos los comandos de ejecución paso a paso que solo afecten al proceso actual.  
  
  ![Volver al principio](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [cambiar procesos, interrumpir y continuar la ejecución, recorrer el código fuente](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
  ![Volver al principio](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contenido](#BKMK_Contents)  
  
###  <a name="BKMK_Break__step__and_continue_commands"></a> Comandos de interrupción, paso y continuación  
  
> [!NOTE]
>  De forma predeterminada, los comandos de interrupción, continuación y paso del depurador afectan a todos los procesos que se depuran. Para cambiar este comportamiento, consulte [configurar el comportamiento de ejecución de varios procesos](#BKMK_Configure_the_execution_behavior_of_multiple_processes)  
  
||||  
|-|-|-|  
|**Comando**|**Interrumpir todos los procesos cuando se interrumpa uno**<br /><br /> Activado (valor predeterminado)|**Interrumpir todos los procesos cuando se interrumpa uno**<br /><br /> Borrado|  
|**Depurar** menú:<br /><br /> -   **Interrumpir todos**|Se interrumpen todos los procesos.|Se interrumpen todos los procesos.|  
|**Depurar** menú:<br /><br /> -   **Continuar**|Se reanudan todos los procesos.|Se reanudan todos los procesos suspendidos.|  
|**Depurar** menú:<br /><br /> -   **Depure paso a paso**<br />-   **Paso a paso**<br />-   **Salir**|Se ejecutan todos los procesos mientras que el proceso actual se ejecuta paso a paso.<br /><br /> A continuación, se interrumpen todos los procesos.|El proceso actual se ejecuta paso a paso.<br /><br /> Se reanudan los procesos suspendidos.<br /><br /> Continúan los procesos en ejecución.|  
|**Depurar** menú:<br /><br /> -   **Ir al proceso actual**<br />-   **Paso a través del proceso actual**<br />-   **Salir del proceso actual**|N/D|El proceso actual se ejecuta paso a paso.<br /><br /> Otros procesos mantienen su estado existente (suspendido o en ejecución).|  
|Ventana de código fuente<br /><br /> -   **Punto de interrupción**|Se interrumpen todos los procesos.|Solo se interrumpe el proceso de la ventana de código fuente.|  
|Menú contextual de la ventana de código fuente:<br /><br /> -   **Ejecutar hasta el cursor**<br /><br /> La ventana de código fuente debe estar en el proceso actual.|Se ejecutan todos los procesos mientras se ejecuta el proceso de la ventana de código fuente hasta el cursor para, a continuación, interrumpirse.<br /><br /> A continuación, se interrumpen todos los demás procesos.|El proceso de la ventana de código fuente se ejecuta hasta el cursor.<br /><br /> Otros procesos mantienen su estado existente (suspendido o en ejecución).|  
|**Procesos** menú contextual de ventana:<br /><br /> -   **Interrumpir proceso**|N/D|Se interrumpe el proceso seleccionado.<br /><br /> Otros procesos mantienen su estado existente (suspendido o en ejecución).|  
|**Procesos** menú contextual de ventana:<br /><br /> -   **Continuar proceso**|N/D|Se reanuda el proceso seleccionado.<br /><br /> Otros procesos mantienen su estado existente (suspendido o en ejecución).|  
  
 ![Volver al principio](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [cambiar procesos, interrumpir y continuar la ejecución, recorrer el código fuente](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 ![Volver al principio](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contenido](#BKMK_Contents)  
  
##  <a name="BKMK_Stop_debugging__terminate_or_detach_from_processes"></a> Detener la depuración, terminar o desasociar procesos  
  
- [Detener, finalización y desasociación de comandos](#BKMK_Stop__terminate__and_detach_commands)  
  
  De forma predeterminada, cuando se elige **depurar**, **Detener depuración** cuando varios procesos están abiertos en el depurador, el depurador finaliza o desasocia de todos los procesos según cómo se abriera el proceso en el depurador:  
  
- Si el proceso actual se inició en el depurador, dicho proceso finalizará.  
  
- Si asoció el depurador al proceso actual, el depurador se desasociará del proceso y dejará el proceso en ejecución.  
  
  Por ejemplo, si inicia la depuración de un proceso de una solución de Visual Studio, asócielo a otro proceso que ya se está ejecutando y, a continuación, elija **Detener depuración**, la sesión de depuración finaliza, el proceso que se inició en Visual Studio se termina, mientras que el proceso que asoció sigue en ejecución. Puede utilizar los siguientes procedimientos para controlar la manera en que se detiene la depuración.  
  
> [!NOTE]
>  El **interrumpir todos los procesos cuando se interrumpa uno** opción no afecta al detener la depuración o finalización y desasociación de procesos.  
  
 **Para cambiar cómo Detener depuración afecta a un proceso individual**  
  
-   Abra el **procesos** ventana (método abreviado **Ctrl + Alt + Z**). Seleccione un proceso y, a continuación, active o desactive el **desasociar cuando se detiene la depuración** casilla de verificación.  
  
###  <a name="BKMK_Stop__terminate__and_detach_commands"></a> Detener, finalización y desasociación de comandos  
  
|||  
|-|-|  
|**Comando**|**Descripción**|  
|**Depurar** menú:<br /><br /> -   **Detener la depuración**|A menos que cambie el comportamiento **procesos** ventana **desasociar cuando se detiene la depuración** opción:<br /><br /> 1.  Finalizan los procesos iniciados por el depurador.<br />2.  Los procesos asociados se desasocian del depurador.|  
|**Depurar** menú:<br /><br /> -   **Finalizar todo**|Finalizan todos los procesos.|  
|**Depurar** menú:<br /><br /> -   **Desasociar todo**|El depurador se desasocia de todos los procesos.|  
|**Procesos** menú contextual de ventana:<br /><br /> -   **Desasociar proceso**|El depurador se desasocia del proceso seleccionado.<br /><br /> Otros procesos mantienen su estado existente (suspendido o en ejecución).|  
|**Procesos** menú contextual de ventana:<br /><br /> -   **Terminar proceso**|Finaliza el proceso seleccionado.<br /><br /> Otros procesos mantienen su estado existente (suspendido o en ejecución).|  
|**Procesos** menú contextual de ventana:<br /><br /> -   **Desasociar cuando se detiene la depuración**|Activa o desactiva el comportamiento de **depurar**, **Detener depuración** para el proceso seleccionado:<br /><br /> -Checked: El depurador se desasocia del proceso.<br />-Desactivada: El proceso ha finalizando.|  
  
 ![Volver al principio](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [detener la depuración, terminar o desasociar procesos](../debugger/debug-multiple-processes.md#BKMK_Stop_debugging__terminate_or_detach_from_processes)  
  
 ![Volver al principio](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contenido](#BKMK_Contents)  
  
## <a name="see-also"></a>Vea también  
 [Especificación de archivos de código fuente y símbolos (.pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Asociar a procesos en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Desplazarse por el código con el depurador](../debugger/navigating-through-code-with-the-debugger.md)   
 [Depuración Just-In-Time](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [Depuración de aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)
