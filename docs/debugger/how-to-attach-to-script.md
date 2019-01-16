---
title: Procedimiento Adjuntar a Script | Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: 73dbb479c7f579739d04a2c378fb984fbba1f72b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53934909"
---
# <a name="how-to-attach-to-script"></a>Procedimiento Asociación a script
En este tema se explica cómo asociar manualmente el depurador de Visual Studio a un archivo de script para el proceso de depuración.  
  
### <a name="to-attach-to-a-running-process"></a>Para asociar a un proceso en ejecución  
  
1. En el menú **Depurar** , elija **Asociar al proceso**. Si no hay proyectos abiertos, elija **Asociar al proceso** en el menú **Herramientas**.  
  
2. En el cuadro de diálogo **Asociar al proceso**, examine la lista **Procesos disponibles** y busque el proceso de script al que desea asociar. Puede identificar los procesos de script examinando la columna **Tipo**.  
  
   1.  Si el proceso que desea depurar se está ejecutando en otro equipo, primero deberá seleccionar el equipo remoto.
  
   2.  Si el proceso se ejecuta con una cuenta de usuario diferente, active la casilla **Mostrar los procesos de todos los usuarios** .  
  
   3.  Si está conectado a través de **Conexión a Escritorio remoto**, active la casilla **Mostrar los procesos de todas las sesiones**.  
  
3. Haga clic en el proceso al que desee asociar.  
  
4. En el **adjuntar a** cuadro, debería ver **código de Script** o **automática: Código de script**. Si ve algo más, siga estos pasos:  
  
   1.  Haga clic en **Seleccionar**.  
  
   2.  En el cuadro de diálogo **Seleccionar tipo de código**, haga clic en **Depurar estos tipos de código** y seleccione **Script**.  
  
   3.  Haga clic en **Aceptar**.  
  
5. Haga clic en **Adjuntar**.  
  
    En este punto, podría ver una advertencia indicando que la depuración de script está deshabilitada en Internet Explorer. Si sucede esto, consulte [advertencia: Depuración de scripts deshabilitada](../debugger/warning-script-debugging-disabled.md)  
  
   La lista **Procesos disponibles** aparecerá automáticamente al abrir el cuadro de diálogo **Procesos** . Los procesos se pueden iniciar y detener en segundo plano mientras el cuadro de diálogo está abierto. Por consiguiente, el contenido podría no estar siempre actualizado. Es posible actualizar la lista en cualquier momento presionando el botón **Actualizar** y ver los procesos en curso.  
  
   Puede tener asociados varios programas mientras realiza la depuración, pero sólo un programa estará activo en el depurador en cada momento. Para establecer el programa activo, puede usar la barra de herramientas Ubicación de depuración. Para obtener más información, vea [Cómo: Establecer el proceso actual](/previous-versions/visualstudio/visual-studio-2010/d5d4sxdw(v=vs.100)).  
  
   Todos los comandos de ejecución del menú **Depurar** afectan al programa activo. Puede interrumpir cualquier programa depurado desde el cuadro de diálogo procesos. Consulte [usar puntos de interrupción](../debugger/using-breakpoints.md).  
  
> [!NOTE]
>  Si intenta asociar a un proceso que pertenece a una cuenta de usuario que no es de confianza, aparecerá un cuadro de diálogo de confirmación con una advertencia de seguridad. Para obtener más información, consulte [advertencia de seguridad: Adjuntar a un proceso que pertenezca a un usuario de confianza puede ser peligroso. Si la información siguiente le resulta sospechosa o no está seguro de su procedencia, no la adjunte a este proceso](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md).  
  
 En algunos casos, al depurar en una sesión de Terminal Services (Escritorio remoto), en la lista Procesos disponibles no aparecerán todos los procesos disponibles. En [!INCLUDE[WinXPSvr](../debugger/includes/winxpsvr_md.md)] o versiones posteriores, si ejecuta Visual Studio como usuario limitado, la lista Procesos disponibles no mostrará los procesos que se ejecuten en la sesión 0, la cual se utiliza para los servicios y otros procesos del servidor, por ejemplo w3wp.exe. Para resolver el problema, ejecute Visual Studio con una cuenta de administrador o ejecute Visual Studio desde la consola de servidor en lugar de una sesión de Servicios de Terminal Server. Si estas soluciones no son posibles, hay una tercera opción: asociar al proceso escribiendo vsjitdebugger.exe-p ProcessId en la línea de comandos de Windows. Puede determinar el identificador de proceso utilizando tlist.exe. Para obtener tlist.exe, descargue e instale las Herramientas de depuración para Windows, disponibles en [Windows Hardware Developer Central](/windows-hardware/drivers/dashboard/).  
  
## <a name="see-also"></a>Vea también  
 [Depuración de scripts en el cliente](../debugger/client-side-script-debugging.md)   
 [Asociar a procesos en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Advertencia de seguridad: Adjuntar a un proceso que pertenezca a un usuario que no sea de confianza puede ser peligroso. Si la información siguiente le resulta sospechosa o no está seguro de su procedencia, no la adjunte a este proceso](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)   
 [Seguridad del depurador](../debugger/debugger-security.md)