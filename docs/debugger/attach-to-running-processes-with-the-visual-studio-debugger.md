---
title: "Crear asociaciones con procesos en ejecuci&#243;n con el depurador de Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.processes.attach"
  - "vs.debug.process"
  - "vs.debug.programs"
  - "vs.debug.detaching"
  - "vs.debug.processes"
  - "vs.debug.error.attach"
  - "vs.debug.remotemachine"
dev_langs: 
  - "C++"
  - "CSharp"
  - "FSharp"
  - "VB"
  - "c++"
helpviewer_keywords: 
  - "depuración remota, asociar a programas"
  - "procesos, asociar a procesos en ejecución"
  - "Cuadro de diálogo Asociar al proceso"
  - "depurar [Visual Studio], asociar a procesos"
  - "depurador, procesos"
ms.assetid: 27900e58-090c-4211-a309-b3e1496d5824
caps.latest.revision: 57
caps.handback.revision: 53
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Crear asociaciones con procesos en ejecuci&#243;n con el depurador de Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Asociar al depurador de Visual Studio a un proceso a menudo es útil cuando no haya iniciado una aplicación desde Visual Studio, pero que desea depurar. Por ejemplo, puede adjuntar a un proceso de IIS o el servicio de Windows que hospeda una aplicación. NET. El proceso de a que adjuntar puede ser local o remoto. Otro ejemplo es que si se está ejecutando la aplicación sin el depurador y se produce una excepción, a continuación, puede asociar al proceso de ejecución de la aplicación para iniciar la depuración.

Para algunos tipos de aplicación (como aplicaciones de la tienda de Windows), no adjuntar directamente a un nombre de proceso, pero usar el **Depurar paquete de aplicaciones instalado** opción de menú en su lugar (consulte la tabla).

Para ayudar a identificar si necesita asociar a un proceso para su escenario, aquí se muestran algunos de los escenarios de depuración más comunes. Cuando existan más instrucciones, proporcionamos los vínculos.

|Escenario|Debug (método)|Nombre del proceso|Tenga en cuenta y vínculos|
|-|-|-|-|
|Depurar cualquier tipo de aplicación compatible en el equipo local al iniciarla desde Visual Studio|Depuración de F5 estándar|N/D|Consulte [Introducción con el depurador](../debugger/getting-started-with-the-debugger.md)|
|Depuración remota ASP.NET 4 o 4.5 en un servidor IIS|Usar herramientas remotas y asociar a proceso|w3wp.exe|Consulte [ASP.NET de depuración remota en un equipo remoto de IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Depuración remota principales de ASP.NET en un servidor IIS|Usar herramientas remotas y asociar a proceso|DNX.exe|Implementación de aplicaciones, consulte [publicar en IIS](https://docs.asp.net/en/latest/publishing/iis.html). Para la depuración, vea [ASP.NET de depuración remota en un equipo remoto de IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Depurar otros tipos de aplicaciones compatibles en un proceso de servidor|Usar herramientas remotas (si el servidor es remoto) y asociar a proceso|Iexplore.exe u otros procesos|Si es necesario, utilice el Administrador de tareas para ayudar a identificar el proceso. Consulte [depuración remota](../debugger/remote-debugging.md) y en las secciones posteriores de este tema|
|Depuración remota de una aplicación de escritorio de Windows|F5 y herramientas remotas|N/D| Consulte [depuración remota](../debugger/remote-debugging.md)|
|Remoto depurar una aplicación Universal de Windows (UWP), OneCore, HoloLens o IoT|Depurar el paquete de aplicación instalada|N/D|Use **depurar / otros destinos de depurar y depurar el paquete de aplicación instalados** en lugar de **adjuntar al proceso**|
|Depurar una aplicación Universal de Windows (UWP), OneCore, HoloLens o IoT iniciada desde Visual Studio|Depurar el paquete de aplicación instalada|N/D|Use **depurar / otros destinos de depurar y depurar el paquete de aplicación instalados** en lugar de **adjuntar al proceso**|
  
> [!WARNING]
>  Para asociar a una aplicación universal de Windows escrita en JavaScript, primero debe habilitar la depuración de la aplicación. Vea [Attach the debugger](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md#BKMK_Attach_the_debugger) en el Centro de desarrollo de Windows.  
  
> [!NOTE]
>  Para que el depurador se asocie al código escrito en C++, el código debe emitir `DebuggableAttribute`. Puede agregar este atributo automáticamente al código vinculando con la opción [/ASSEMBLYDEBUG](/visual-cpp/build/reference/assemblydebug-add-debuggableattribute) del vinculador.

## <a name="what-debugger-features-can-i-use"></a>¿Qué características del depurador se debe usar?

Para usar todas las características del depurador de Visual Studio (como alcanzar puntos de interrupción), el archivo ejecutable debe coincidir exactamente con el origen local y símbolos (es decir, el depurador debe poder cargar correcto [(.pbd) archivos de símbolos](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)). De forma predeterminada, esto requiere una compilación de depuración.

Para escenarios de depuración remota, debe tener el código fuente una copia del código fuente está abierto en Visual Studio. Los archivos binarios de la aplicación compilada en el equipo remoto deben proceder de la misma versión de compilación como en el equipo local.

En algunos escenarios de depuración locales, puede depurar en Visual Studio sin acceso al origen si los archivos de símbolos correctos están presentes con la aplicación (de forma predeterminada, esto requiere una compilación de depuración). Para obtener más información, consulte [especificar archivos de código fuente y símbolos](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

Para aplicaciones de escritorio de Windows, también puede depurar la aplicación en ejecución mediante el depurador JIT (Visual Studio se abre e interrumpir el código de la aplicación cuando se produce un error).

##  <a name="a-namebkmkattachtoaprocessonaremotecomputera-attach-to-a-process-on-a-remote-computer"></a><a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> Asociar a un proceso en un equipo remoto  
 Para asociar a un proceso, debe conocer el nombre del proceso. Para las aplicaciones ASP.NET que se han implementado en IIS, consulte [ASP.NET de depuración remota en un equipo IIS remoto](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) o [publicar en IIS](https://docs.asp.net/en/latest/publishing/iis.html) para aplicaciones ASP.NET Core. En el caso de las demás aplicaciones, encontrará el nombre del proceso en el Administrador de tareas.
  
 En el cuadro de diálogo **Asociar al proceso** , puede seleccionar otro equipo configurado para la depuración remota. Para obtener más información, consulte [depuración remota](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md). Cuando se ha seleccionado un equipo remoto, se puede consultar una lista con los procesos disponibles que se están ejecutando en dicho equipo y establecer una asociación con uno o varios procesos para llevar a cabo la depuración.
  
 **Para seleccionar un equipo remoto:**  

1. En Visual Studio, seleccione **Depurar / Asociar al proceso**.

2.  En el cuadro **Asociar al proceso** , seleccione el tipo de conexión adecuado en la lista **Transporte** . **Valor predeterminado** es la configuración correcta en la mayoría de los casos.

    La configuración de **Transporte** se conserva entre las sesiones de depuración. 
  
3.  Utilice el cuadro de lista **Calificador** para elegir el nombre del equipo remoto mediante uno de los métodos siguientes:  
  
    1.  Escriba el nombre en el cuadro de lista **Calificador** .
    
        >**Nota** Si, en pasos posteriores, no se puede conectar con el nombre del equipo remoto, utilice la dirección IP. (El número de puerto puede aparecer automáticamente después de seleccionar el proceso. También puede escribir manualmente. En la siguiente ilustración, 4020 es el puerto predeterminado para el depurador remoto.)  
  
    2.  Haga clic en la flecha desplegable del cuadro de lista **Calificador** y seleccione el nombre del equipo en la lista desplegable.  
  
    3.  Haga clic en el botón **Buscar** situado junto a la lista**Calificador** para abrir el cuadro de diálogo **Seleccionar conexión del depurador remoto** . El cuadro **Seleccionar conexión del depurador remoto** muestra todos los dispositivos que se encuentran en su subred local, y cualquier dispositivo conectado directamente al equipo mediante un cable Ethernet. Haga clic en el equipo o el dispositivo que desee y, a continuación, haga clic en **Seleccionar**. 
    
    ![DBG_Basics_Attach_To_Process](../debugger/media/dbg_basics_attach_to_process.png "DBG_Basics_Attach_To_Process") 
  
     La configuración de **Calificador** sólo se conserva entre las sesiones de depuración si se produce una conexión de depuración correcta con ese calificador.
     
4.  Haga clic en **Actualizar**.

      La lista **Procesos disponibles** aparecerá automáticamente al abrir el cuadro de diálogo **Procesos** . Los procesos se pueden iniciar y detener en segundo plano mientras el cuadro de diálogo está abierto. Sin embargo, el contenido no siempre estará actualizado. Es posible actualizar la lista en cualquier momento y ver los procesos en curso haciendo clic en **Actualizar**. 
     
4.  En el cuadro de diálogo **Asociar al proceso** , seleccione el programa que desea asociar en la lista **Procesos disponibles** .  
  
     Si el proceso se ejecuta con una cuenta de usuario diferente, active la casilla **Mostrar los procesos de todos los usuarios** .
     
5.  Haga clic en **Asociar**.  
  
##  <a name="a-namebkmkattachtoarunningprocessa-attach-to-a-running-process-on-the-local-machine"></a><a name="BKMK_Attach_to_a_running_process"></a> Adjuntar a un proceso en ejecución en el equipo local  
 Para asociar a un proceso, debe conocer el nombre del proceso.  Encontrará el nombre del proceso en el Administrador de tareas.  
  
1.  En Visual Studio, seleccione **Depurar / Asociar al proceso**.
  
2.  En el cuadro de diálogo **Asociar al proceso** , seleccione el programa que desea asociar en la lista **Procesos disponibles** .  
  
     Si el proceso se ejecuta con una cuenta de usuario diferente, active la casilla **Mostrar los procesos de todos los usuarios** .
  
3.  En el cuadro **Asociar a** , asegúrese de que aparece el tipo de código que quiere depurar. El valor predeterminado **Automático** intenta determinar qué tipo de código desea depurar. Para establecer el tipo de código manualmente, haga lo siguiente:  
  
    1.  En el cuadro de diálogo **Asociar a** , haga clic en **Seleccionar**.  
  
    2.  En el cuadro de diálogo **Seleccionar tipo de código** , haga clic en **Depurar estos tipos de código** y seleccione los tipos que va a depurar.  
  
    3.  Haga clic en **Aceptar**.  
  
4.  Haga clic en **Asociar**.

## <a name="additional-info"></a>Información adicional

Puede tener asociados varios programas mientras realiza la depuración, pero sólo un programa estará activo en el depurador en cada momento. Puede establecer el programa activo en la barra de herramientas **Ubicación de depuración** o en la ventana **Procesos** . Para obtener más información, vea [Cómo: Establecer el programa actual](http://msdn.microsoft.com/es-es/7e1d7fa5-0e40-44cf-8c41-d3dba31c969e).  
  
Si intenta asociar a un proceso que pertenece a una cuenta de usuario que no es de confianza, aparecerá un cuadro de diálogo de confirmación con una advertencia de seguridad. Para obtener más información, consulte [Advertencia de seguridad: adjuntar a un proceso que pertenece a un usuario de confianza puede ser peligroso. Si la información siguiente parece sospechosa o no está seguro, no asocie a este proceso](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md).  
  
En algunos casos, al depurar en una sesión de Escritorio remoto (Terminal Services), en la lista **Procesos disponibles** no aparecerán todos los procesos disponibles. Si se ejecuta Visual Studio como usuario que tiene una cuenta de usuario limitada, la lista **Procesos disponibles** no mostrará los procesos que se estén ejecutando en la sesión 0, la cual se usa para los servicios y otros procesos de servidor, incluido w3wp.exe. Para resolver el problema, ejecute [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] con una cuenta de administrador o ejecute [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] desde la consola de servidor en lugar de una sesión de Terminal Services. Si ninguna de estas dos soluciones es posible, existe una tercera opción que consiste en asociar al proceso mediante la ejecución de `vsjitdebugger.exe -p` *ProcessId* en la línea de comandos de Windows. Puede determinar el identificador de proceso mediante tlist.exe. Para obtener el archivo tlist.exe, descargue e instale las Herramientas de depuración para Windows, disponibles en  [Descargas de WDK y WinDbg](http://go.microsoft.com/fwlink/?LinkId=168279).
  
##  <a name="a-namebkmktroubleshootattacherrorsa-troubleshoot-attach-errors"></a><a name="BKMK_Troubleshoot_attach_errors"></a> Solucionar problemas de errores de asociación  
 Cuando el depurador se asocia a un proceso en ejecución, el proceso puede contener uno o varios tipos de código. Los tipos de código a los que se puede asociar el depurador se muestran y seleccionan en el cuadro de diálogo **Seleccionar tipo de código** .  
  
 A veces, el depurador puede asociarse correctamente a un tipo de código, pero no a otro. Esto puede ocurrir cuando se intenta asociar el depurador a un proceso que está ejecutándose en un equipo remoto. Puede que el equipo remoto tenga instalados los componentes de depuración remota para algunos tipos de código, pero no para otros. También puede ocurrir al intentar asociar el depurador a dos o varios procesos para realizar una depuración directa de la base de datos. La depuración de SQL sólo admite la asociación a un único proceso.  
  
 Si el depurador logra asociarse a algunos tipos de código, pero no a todos, aparecerá un mensaje en el que se identifican los tipos sin asociar:  
  
 Si el depurador se asocia correctamente a un tipo de código por lo menos, podrá reanudar la depuración del proceso. Sólo podrá depurar los tipos de código que se hayan asociado correctamente. El mensaje de ejemplo anterior indica que el tipo de código de script no se ha asociado correctamente. Por lo tanto, no podrá depurar código de script dentro del proceso. El código de script del proceso seguirá ejecutándose, pero no se podrán establecer puntos de interrupción, ni se podrán ver los datos, ni se podrá realizar ninguna otra operación de depuración en el script.  
  
 Si desea obtener información más detallada sobre el motivo por el que el depurador no se ha asociado correctamente a un tipo de código, puede intentar asociarlo de nuevo con ese tipo de código exclusivamente.  
  
 **Para obtener información específica acerca de por qué un tipo de código no se pudo conectar**  
  
1.  Desasocie el proceso. En el menú **Depurar** , haga clic en **Desasociar todo**.  
  
2.  Vuelva a asociar el proceso, pero seleccionando un único tipo de código.  
  
    1.  En el cuadro de diálogo **Asociar al proceso** , seleccione el proceso en la lista **Procesos disponibles** .  
  
    2.  Haga clic en **Seleccionar**.  
  
    3.  En el cuadro de diálogo **Seleccionar tipo de código** , seleccione **Depurar estos tipos de código** y el tipo de código que no se haya asociado correctamente. Borre cualquier otro código.  
  
    4.  Haga clic en **Aceptar**. El cuadro de diálogo **Seleccionar tipo de código** se cierra.  
  
    5.  En el cuadro de diálogo **Asociar al proceso** , haga clic en **Asociar**.  
  
     Esta vez se producirá un error en todo el proceso de asociación y aparecerá un mensaje de error específico.  
  
## <a name="see-also"></a>Vea también  
 [Depurar múltiples procesos](../debugger/debug-multiple-processes.md)   
 [Depuración Just-In-Time](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [Depuración remota](../debugger/remote-debugging.md)