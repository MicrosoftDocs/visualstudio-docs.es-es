---
title: 'Error: Error de inicio de sesión remoto del grupo de trabajo | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d0157b18c0b0dfce2ba69482dc1c61e1ddf3a996
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58998046"
---
# <a name="error-workgroup-remote-logon-failure"></a>Error: Error de inicio de sesión del grupo de trabajo de forma remota
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este error reza como sigue:  
  
 Error de inicio de sesión: nombre de usuario desconocido o contraseña incorrecta  
  
 **Causa**  
  
 Este error se produce cuando se está depurando en un equipo de un grupo de trabajo y se intenta conectar con el equipo remoto. Entre las posibles causas se incluyen:  
  
-   No existe ninguna cuenta que coincida con el nombre y la contraseña en el equipo remoto.  
  
-   Si el equipo de Visual Studio y la máquina remota están en grupos de trabajo, el error se podría producir debido a la configuración predeterminada de la **Directiva de seguridad local** de la máquina remota. La configuración predeterminada de la **Directiva de seguridad local** es **Solo invitado: los usuarios locales se autentican como invitados**. Para depurar en esta configuración, es necesario cambiar la configuración del equipo remoto a **Clásico: usuarios locales autenticados como ellos mismos**.  
  
> [!NOTE]
>  Debe ser administrador para llevar a cabo las tareas siguientes.  
  
### <a name="to-open-the-local-security-policy-window"></a>Para abrir la ventana Directiva de seguridad local  
  
1.  Inicie el complemento **secpol.msc** en Microsoft Management Console. Escriba secpol.msc en la búsqueda de Windows, el cuadro Ejecutar de Windows o en un símbolo del sistema.  
  
### <a name="to-add-user-rights-assignments"></a>Para agregar asignaciones de derechos de usuario  
  
1.  1  
  
2.  Abra la ventana **Directiva de seguridad local**.  
  
3.  Expanda la carpeta **Directivas locales**.  
  
4.  Haga clic en **Asignación de derechos de usuario**.  
  
5.  En la columna **Directiva**, haga doble clic en **Depurar programas** para ver las asignaciones actuales de la directiva de grupo local en el cuadro de diálogo **Configuración de directiva de seguridad local**.  
  
     ![Derechos de usuario de directiva de seguridad local](../debugger/media/dbg-err-localsecuritypolicy-userrightsdebugprograms.png "DBG_ERR_LocalSecurityPolicy_UserRightsDebugPrograms")  
  
6.  Para agregar nuevos usuarios, haga clic en el botón **Agregar usuario o grupo**.  
  
### <a name="to-change-the-sharing-and-security-model"></a>Para cambiar el modelo de seguridad y recursos compartidos  
  
1.  Abra la ventana **Directiva de seguridad local**.  
  
2.  Expanda la carpeta **Directivas locales**.  
  
3.  Haga clic en **Opciones de seguridad**.  
  
4.  En el **directiva** columna, haga doble clic en **acceso de red: Modelo de seguridad y recursos compartidos para cuentas locales**.  
  
5.  En el **acceso de red: Modelo de seguridad y recursos compartidos para cuentas locales** diálogo cuadro, cambie el valor a **clásico: usuarios locales autenticados como ellos mismos** y haga clic en el **aplicar** botón.  
  
     ![Opciones de seguridad de directiva de seguridad local](../debugger/media/dbg-err-localsecuritypolicy-securityoptions-networkaccess.png "DBG_ERR_LocalSecurityPolicy_SecurityOptions_NetworkAccess")  
  
## <a name="see-also"></a>Vea también  
 [Errores de la depuración remota y sus soluciones](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remote Debugging](../debugger/remote-debugging.md)
