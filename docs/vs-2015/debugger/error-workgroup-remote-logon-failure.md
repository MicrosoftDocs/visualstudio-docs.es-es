---
title: 'Error: Error de inicio de sesión remoto del grupo de trabajo | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.workgroup_remote_logon_failure
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- logon failure, remote debugging
- remote debugging, logon failure
ms.assetid: 7be2c5bb-40fe-48d6-8cfc-c231fbd3d64e
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 489fb331f08c95bf26a9b99c1143575aaa44257f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49236033"
---
# <a name="error-workgroup-remote-logon-failure"></a>Error: El grupo de trabajo no ha podido iniciar una sesión remota
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este error reza como sigue:  
  
 Error de inicio de sesión: nombre de usuario desconocido o contraseña incorrecta  
  
 **Causa**  
  
 Este error se produce cuando se está depurando en un equipo de un grupo de trabajo y se intenta conectar con el equipo remoto. Entre las posibles causas se incluyen:  
  
-   No existe ninguna cuenta que coincida con el nombre y la contraseña en el equipo remoto.  
  
-   Si el equipo de Visual Studio y la máquina remota están en grupos de trabajo, este error puede deberse a que el valor predeterminado **directiva de seguridad Local** establecer en el equipo remoto. La configuración predeterminada para el **directiva de seguridad Local** configuración es **sólo invitado: usuarios locales autenticados como invitados**. Para depurar en esta configuración, debe cambiar la configuración en el equipo remoto a **clásico: usuarios locales autenticados como ellos mismos**.  
  
> [!NOTE]
>  Debe ser administrador para llevar a cabo las tareas siguientes.  
  
### <a name="to-open-the-local-security-policy-window"></a>Para abrir la ventana Directiva de seguridad local  
  
1.  Iniciar el **secpol.msc** complemento Microsoft Management Console. Escriba secpol.msc en la búsqueda de Windows, el cuadro Ejecutar de Windows o en un símbolo del sistema.  
  
### <a name="to-add-user-rights-assignments"></a>Para agregar asignaciones de derechos de usuario  
  
1.  1  
  
2.  Abra el **directiva de seguridad Local** ventana.  
  
3.  Expanda el **directivas locales** carpeta.  
  
4.  Haga clic en **asignación de derechos de usuario**.  
  
5.  En el **directiva** columna, haga doble clic en **depurar programas** para ver las asignaciones de directivas de grupo local actual en el **configuración de directiva de seguridad Local** cuadro de diálogo.  
  
     ![Derechos de usuario de directiva de seguridad local](../debugger/media/dbg-err-localsecuritypolicy-userrightsdebugprograms.png "DBG_ERR_LocalSecurityPolicy_UserRightsDebugPrograms")  
  
6.  Para agregar nuevos usuarios, haga clic en el **Agregar usuario o grupo** botón.  
  
### <a name="to-change-the-sharing-and-security-model"></a>Para cambiar el modelo de seguridad y recursos compartidos  
  
1.  Abra el **directiva de seguridad Local** ventana.  
  
2.  Expanda el **directivas locales** carpeta.  
  
3.  Haga clic en **las opciones de seguridad**.  
  
4.  En el **directiva** columna, haga doble clic en **acceso de red: modelo de seguridad y recursos compartidos para cuentas locales**.  
  
5.  En el **acceso de red: modelo de seguridad y recursos compartidos para cuentas locales** cuadro de diálogo, cambie el valor a **clásico: usuarios locales autenticados como ellos mismos** y haga clic en el **aplicar**botón.  
  
     ![Opciones de seguridad de directiva de seguridad local](../debugger/media/dbg-err-localsecuritypolicy-securityoptions-networkaccess.png "DBG_ERR_LocalSecurityPolicy_SecurityOptions_NetworkAccess")  
  
## <a name="see-also"></a>Vea también  
 [Errores de depuración remota y sus soluciones](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remote Debugging](../debugger/remote-debugging.md)



