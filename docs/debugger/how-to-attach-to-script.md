---
title: "C&#243;mo: Adjuntar a script | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "procesos, adjuntar a script"
  - "depuración remota, adjuntar a script"
  - "depuración de secuencias de comandos, adjuntar a script"
  - "script, adjuntar a"
ms.assetid: 82013e9a-ef53-4fd2-b451-a6891cdc6307
caps.latest.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 23
---
# C&#243;mo: Adjuntar a script
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En este tema se explica cómo asociar manualmente el depurador de Visual Studio a un archivo de script para el proceso de depuración.  
  
### Para asociar a un proceso en ejecución  
  
1.  En el menú **Depurar**, elija **Asociar al proceso**. \(Si no hay proyectos abiertos, elija **Asociar al proceso** en el menú **Herramientas**\).  
  
2.  En el cuadro de diálogo **Asociar al proceso**, examine la lista **Procesos disponibles** y busque el proceso de script al que desea asociar.  Puede identificar los procesos de script examinando la columna **Tipo**.  
  
    1.  Si el proceso que desea depurar se está ejecutando en otro equipo, primero deberá seleccionar el equipo remoto.  Para obtener más información, vea [How to: Select a Remote Computer](http://msdn.microsoft.com/es-es/4332ba8e-2f0b-4f62-b96a-e762b9f3c3ba).  
  
    2.  Si el proceso se ejecuta con una cuenta de usuario diferente, active la casilla **Mostrar los procesos de todos los usuarios**.  
  
    3.  Si está conectado a través de **Conexión a Escritorio remoto**, active la casilla **Mostrar los procesos de todas las sesiones**.  
  
3.  Haga clic en el proceso al que desee asociar.  
  
4.  En el cuadro **Asociar a**, debe ver **Código de script** o **Automático: código de script**.  Si ve algo más, siga estos pasos:  
  
    1.  Haga clic en **Seleccionar**.  
  
    2.  En el cuadro de diálogo **Seleccionar tipo de código**, haga clic en **Depurar estos tipos de código** y seleccione **Script**.  
  
    3.  Haga clic en **Aceptar**.  
  
5.  Haga clic en **Asociar**.  
  
     En este punto, podría ver una advertencia indicando que la depuración de script está deshabilitada en Internet Explorer.  Si esto sucede, vea [Advertencia: Depuración de script deshabilitada](../debugger/warning-script-debugging-disabled.md).  
  
 La lista **Procesos disponibles** aparecerá automáticamente al abrir el cuadro de diálogo **Procesos**.  Los procesos se pueden iniciar y detener en segundo plano mientras el cuadro de diálogo está abierto.  Por consiguiente, el contenido podría no estar siempre actualizado.  Es posible actualizar la lista en cualquier momento presionando el botón **Actualizar** y ver los procesos en curso.  
  
 Puede tener asociados varios programas mientras realiza la depuración, pero sólo un programa estará activo en el depurador en cada momento.  Para establecer el programa activo, puede usar la barra de herramientas Ubicación de depuración.  Para obtener más información, vea [How to: Set the Current Process](http://msdn.microsoft.com/es-es/7e1d7fa5-0e40-44cf-8c41-d3dba31c969e).  
  
 Todos los comandos de ejecución del menú **Depurar** afectan al programa activo.  Puede interrumpir cualquier programa depurado desde el cuadro de diálogo Procesos. Vea [Usar puntos de interrupción](../debugger/using-breakpoints.md).  
  
> [!NOTE]
>  Si intenta asociar a un proceso que pertenece a una cuenta de usuario que no es de confianza, aparecerá un cuadro de diálogo de confirmación con una advertencia de seguridad.  Para obtener más información, vea [Advertencia de seguridad: adjuntar a un proceso que pertenezca a una cuenta de usuario que no sea de confianza puede ser peligroso. Si la información siguiente le resulta sospechosa o no está seguro de su procedencia, no la adjunte a este proceso.](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md).  
  
 En algunos casos, al depurar en una sesión de Terminal Services \(Escritorio remoto\), en la lista Procesos disponibles no aparecerán todos los procesos disponibles.  En [!INCLUDE[WinXPSvr](../debugger/includes/winxpsvr_md.md)] o versiones posteriores, si ejecuta Visual Studio como usuario limitado, la lista Procesos disponibles no mostrará los procesos que se ejecuten en la sesión 0, la cual se utiliza para los servicios y otros procesos del servidor, por ejemplo w3wp.exe.  Para resolver el problema, ejecute Visual Studio con una cuenta de administrador o ejecute Visual Studio desde la consola de servidor en lugar de una sesión de Servicios de Terminal Server.  Si estas soluciones no son posibles, hay una tercera opción: asociar al proceso escribiendo vsjitdebugger.exe\-p ProcessId en la línea de comandos de Windows.  Puede determinar el identificador de proceso utilizando tlist.exe.  Para obtener tlist.exe, descargue e instale las Herramientas de depuración para Windows, disponibles en [Windows Hardware Developer Central](http://go.microsoft.com/fwlink/?linkid=1651).  
  
## Vea también  
 [Depuración de secuencias de comandos en el cliente](../debugger/client-side-script-debugging.md)   
 [Crear asociaciones con procesos en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Advertencia de seguridad: adjuntar a un proceso que pertenezca a una cuenta de usuario que no sea de confianza puede ser peligroso. Si la información siguiente le resulta sospechosa o no está seguro de su procedencia, no la adjunte a este proceso.](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md)   
 [Seguridad del depurador](../debugger/debugger-security.md)