---
title: 'Cómo: adjuntar a Script | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 66f9ceb4d89c2c33e903811b891438d130f5552b
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2018
ms.locfileid: "44284011"
---
# <a name="how-to-attach-to-script"></a>Cómo: Adjuntar a script
En este tema se explica cómo asociar manualmente el depurador de Visual Studio a un archivo de script para el proceso de depuración.  
  
### <a name="to-attach-to-a-running-process"></a>Para asociar a un proceso en ejecución  
  
1.  En el menú **Depurar** , elija **Asociar al proceso**. (Si no hay ningún proyecto está abierto, elija **asociar al proceso** en el **herramientas** menú.)  
  
2.  En el **asociar al proceso** cuadro de diálogo, examine la **procesos disponibles** lista y busque el proceso de script desean asociar. Puede identificar los procesos de script examinando la **tipo** columna.  
  
    1.  Si el proceso que desea depurar se está ejecutando en otro equipo, primero deberá seleccionar el equipo remoto.
  
    2.  Si el proceso se ejecuta con una cuenta de usuario diferente, active la casilla **Mostrar los procesos de todos los usuarios** .  
  
    3.  Si está conectado a través de **conexión a Escritorio remoto**, seleccione el **mostrar los procesos de todas las sesiones** casilla de verificación.  
  
3.  Haga clic en el proceso al que desee asociar.  
  
4.  En el **adjuntar a** cuadro, debería ver **código de Script** o **automático: código de Script**. Si ve algo más, siga estos pasos:  
  
    1.  Haga clic en **Seleccionar**.  
  
    2.  En el **Seleccionar tipo de código** cuadro de diálogo, haga clic en **depurar estos tipos de código** y seleccione **Script**.  
  
    3.  Haga clic en **Aceptar**.  
  
5.  Haga clic en **Adjuntar**.  
  
     En este punto, podría ver una advertencia indicando que la depuración de script está deshabilitada en Internet Explorer. Si sucede esto, consulte [advertencia: depuración de scripts deshabilitada](../debugger/warning-script-debugging-disabled.md).  
  
 La lista **Procesos disponibles** aparecerá automáticamente al abrir el cuadro de diálogo **Procesos** . Los procesos se pueden iniciar y detener en segundo plano mientras el cuadro de diálogo está abierto. Por consiguiente, el contenido podría no estar siempre actualizado. Puede actualizar la lista en cualquier momento para ver la lista actual de procesos presionando el **actualizar** botón.  
  
 Puede tener asociados varios programas mientras realiza la depuración, pero sólo un programa estará activo en el depurador en cada momento. Para establecer el programa activo, puede usar la barra de herramientas Ubicación de depuración. Para obtener más información, consulte [Cómo: establecer el proceso actual](/previous-versions/visualstudio/visual-studio-2010/d5d4sxdw(v=vs.100)).  
  
 Todos los **depurar** comandos de menú de ejecución afectan al programa activo. Puede interrumpir cualquier programa depurado desde el cuadro de diálogo procesos. Consulte [usar puntos de interrupción](../debugger/using-breakpoints.md).  
  
> [!NOTE]
>  Si intenta asociar a un proceso que pertenece a una cuenta de usuario que no es de confianza, aparecerá un cuadro de diálogo de confirmación con una advertencia de seguridad. Para obtener más información, consulte [advertencia de seguridad: adjuntar a un proceso que pertenezca a un usuario de confianza puede ser peligroso. Si la información siguiente parece sospechosa o no está seguro, no la adjunte a este proceso](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md).  
  
 En algunos casos, al depurar en una sesión de Terminal Services (Escritorio remoto), en la lista Procesos disponibles no aparecerán todos los procesos disponibles. En [!INCLUDE[WinXPSvr](../debugger/includes/winxpsvr_md.md)] o versiones posteriores, si ejecuta Visual Studio como usuario limitado, la lista Procesos disponibles no mostrará los procesos que se ejecuten en la sesión 0, la cual se utiliza para los servicios y otros procesos del servidor, por ejemplo w3wp.exe. Para resolver el problema, ejecute Visual Studio con una cuenta de administrador o ejecute Visual Studio desde la consola de servidor en lugar de una sesión de Servicios de Terminal Server. Si ninguna de estas dos soluciones es posible, una tercera opción es asociar al proceso escribiendo vsjitdebugger.exe -p ProcessId en la línea de comandos de Windows. Puede determinar el identificador de proceso utilizando tlist.exe. Para obtener tlist.exe, descargue e instale las herramientas de depuración para Windows, disponible en [Windows Hardware Developer Central](/windows-hardware/drivers/dashboard/).  
  
## <a name="see-also"></a>Vea también  
 [Depuración de scripts del lado cliente](../debugger/client-side-script-debugging.md)   
 [Adjuntar a procesos en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Advertencia de seguridad: Adjuntar a un proceso que pertenezca a un usuario que no sea de confianza puede ser peligroso. Si la información siguiente parece sospechosa o no está seguro, no la adjunte a este proceso](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)   
 [Seguridad del depurador](../debugger/debugger-security.md)