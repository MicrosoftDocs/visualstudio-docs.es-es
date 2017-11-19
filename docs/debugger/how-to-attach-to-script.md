---
title: "Cómo: adjuntar a Script | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- script debugging, attaching to script
- script, attaching to
- processes, attaching to script
- remote debugging, attaching to script
ms.assetid: 82013e9a-ef53-4fd2-b451-a6891cdc6307
caps.latest.revision: "23"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 914974e27e6856174a4260b741f2e864d8509ff8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-attach-to-script"></a>Cómo: Adjuntar a script
En este tema se explica cómo asociar manualmente el depurador de Visual Studio a un archivo de script para el proceso de depuración.  
  
### <a name="to-attach-to-a-running-process"></a>Para asociar a un proceso en ejecución  
  
1.  En el menú **Depurar** , elija **Asociar al proceso**. (Si no hay proyectos abiertos, elija **adjuntar al proceso** en el **herramientas** menú.)  
  
2.  En el **adjuntar al proceso** cuadro de diálogo, consulte el **procesos disponibles** lista y busque el proceso de script desean adjuntar a. Puede identificar los procesos de script examinando la **tipo** columna.  
  
    1.  Si el proceso que desea depurar se está ejecutando en otro equipo, primero deberá seleccionar el equipo remoto. Para obtener más información, consulte [Cómo: seleccionar un equipo remoto](http://msdn.microsoft.com/en-us/4332ba8e-2f0b-4f62-b96a-e762b9f3c3ba).  
  
    2.  Si el proceso se ejecuta con una cuenta de usuario diferente, active la casilla **Mostrar los procesos de todos los usuarios** .  
  
    3.  Si está conectado a través de **conexión a Escritorio remoto**, seleccione la **mostrar los procesos de todas las sesiones** casilla de verificación.  
  
3.  Haga clic en el proceso al que desee asociar.  
  
4.  En el **adjuntar a** cuadro, debería ver **código de Script** o **automático: código de Script**. Si ve algo más, siga estos pasos:  
  
    1.  Haga clic en **Seleccionar**.  
  
    2.  En el **Seleccionar tipo de código** cuadro de diálogo, haga clic en **depurar estos tipos de código** y seleccione **Script**.  
  
    3.  Haga clic en **Aceptar**.  
  
5.  Haga clic en **Adjuntar**.  
  
     En este punto, podría ver una advertencia indicando que la depuración de script está deshabilitada en Internet Explorer. Si sucede esto, consulte [advertencia: depuración de scripts deshabilitada](../debugger/warning-script-debugging-disabled.md).  
  
 La lista **Procesos disponibles** aparecerá automáticamente al abrir el cuadro de diálogo **Procesos** . Los procesos se pueden iniciar y detener en segundo plano mientras el cuadro de diálogo está abierto. Por consiguiente, el contenido podría no estar siempre actualizado. Puede actualizar la lista en cualquier momento para ver la lista actual de procesos presionando el **actualizar** botón.  
  
 Puede tener asociados varios programas mientras realiza la depuración, pero sólo un programa estará activo en el depurador en cada momento. Para establecer el programa activo, puede usar la barra de herramientas Ubicación de depuración. Para obtener más información, consulte [Cómo: establecer el proceso actual](http://msdn.microsoft.com/en-us/7e1d7fa5-0e40-44cf-8c41-d3dba31c969e).  
  
 Todos los **depurar** comandos de ejecución del menú afectan al programa activo. Puede interrumpir todos los programas depurados desde el cuadro de diálogo procesos. Vea [usar puntos de interrupción](../debugger/using-breakpoints.md).  
  
> [!NOTE]
>  Si intenta asociar a un proceso que pertenece a una cuenta de usuario que no es de confianza, aparecerá un cuadro de diálogo de confirmación con una advertencia de seguridad. Para obtener más información, vea [advertencia de seguridad: la asociación a un proceso que pertenece a un usuario de confianza puede ser peligrosa. Si la información siguiente parece sospechosa o no está seguro, no se conecte a este proceso](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md).  
  
 En algunos casos, al depurar en una sesión de Terminal Services (Escritorio remoto), en la lista Procesos disponibles no aparecerán todos los procesos disponibles. En [!INCLUDE[WinXPSvr](../debugger/includes/winxpsvr_md.md)] o versiones posteriores, si ejecuta Visual Studio como usuario limitado, la lista Procesos disponibles no mostrará los procesos que se ejecuten en la sesión 0, la cual se utiliza para los servicios y otros procesos del servidor, por ejemplo w3wp.exe. Para resolver el problema, ejecute Visual Studio con una cuenta de administrador o ejecute Visual Studio desde la consola de servidor en lugar de una sesión de Servicios de Terminal Server. Si ninguna de estas dos soluciones es posible, una tercera opción consiste en asociar al proceso escribiendo vsjitdebugger.exe -p ProcessId en la línea de comandos de Windows. Puede determinar el identificador de proceso utilizando tlist.exe. Para obtener tlist.exe, descargue e instale las herramientas de depuración para Windows, disponible en [Windows Hardware Developer Central](http://go.microsoft.com/fwlink/?linkid=1651).  
  
## <a name="see-also"></a>Vea también  
 [Depuración de Script de cliente](../debugger/client-side-script-debugging.md)   
 [Adjuntar a procesos en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Advertencia de seguridad: Adjuntar a un proceso que pertenezca a un usuario que no sea de confianza puede ser peligroso. Si la información siguiente parece sospechosa o no está seguro, no se conecte a este proceso](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md)   
 [Seguridad del depurador](../debugger/debugger-security.md)