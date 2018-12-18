---
title: 'Error: Error de inicio de sesión remoto del grupo de trabajo | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.workgroup_remote_logon_failure
dev_langs:
- CSharp
- VB
- FSharp
- JScript
- C++
helpviewer_keywords:
- logon failure, remote debugging
- remote debugging, logon failure
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 60cee4e6bdb4ebab925325695eb9ad6813929879
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
ms.locfileid: "31482001"
---
# <a name="error-workgroup-remote-logon-failure"></a>Error: El grupo de trabajo no ha podido iniciar una sesión remota
Este error reza como sigue:  
  
 Error de inicio de sesión: nombre de usuario desconocido o contraseña incorrecta  
  
 **Causa**  
  
 Este error se produce cuando se está depurando en un equipo de un grupo de trabajo y se intenta conectar con el equipo remoto. Entre las posibles causas se incluyen:  
  
-   No existe ninguna cuenta que coincida con el nombre y la contraseña en el equipo remoto.  
  
-   Si el equipo de Visual Studio y el equipo remoto se encuentran en grupos de trabajo, este error puede deberse a que el valor predeterminado **directiva de seguridad Local** establecer en el equipo remoto. El valor predeterminado para la **directiva de seguridad Local** configuración es **sólo invitado: usuarios locales autenticados como invitados**. Para depurar en esta configuración, debe cambiar la configuración en el equipo remoto a **clásico: usuarios locales autenticados como ellos mismos**.  
  
> [!NOTE]
>  Debe ser administrador para llevar a cabo las tareas siguientes.  
  
### <a name="to-open-the-local-security-policy-window"></a>Para abrir la ventana Directiva de seguridad local  
  
1.  Iniciar el **secpol.msc** complemento Microsoft Management Console. Escriba secpol.msc en la búsqueda de Windows, el cuadro Ejecutar de Windows o en un símbolo del sistema.  
  
### <a name="to-add-user-rights-assignments"></a>Para agregar asignaciones de derechos de usuario  
  
1.  Abra la **directiva de seguridad Local** ventana.  
  
2.  Expanda el **directivas locales** carpeta.  
  
3.  Haga clic en **asignación de derechos de usuario**.  
  
4.  En el **directiva** columna, haga doble clic en **depurar programas** para ver las asignaciones de directivas de grupo local actual en el **configuración de directiva de seguridad Local** cuadro de diálogo.  
  
     ![Derechos de usuario de directiva de seguridad local](../debugger/media/dbg_err_localsecuritypolicy_userrightsdebugprograms.png "DBG_ERR_LocalSecurityPolicy_UserRightsDebugPrograms")  
  
5.  Para agregar nuevos usuarios, haga clic en el **Agregar usuario o grupo** botón.  
  
### <a name="to-change-the-sharing-and-security-model"></a>Para cambiar el modelo de seguridad y recursos compartidos  
  
1.  Abra la **directiva de seguridad Local** ventana.  
  
2.  Expanda el **directivas locales** carpeta.  
  
3.  Haga clic en **opciones de seguridad**.  
  
4.  En el **directiva** columna, haga doble clic en **acceso a la red: modelo de seguridad y recursos compartidos para cuentas locales**.  
  
5.  En el **acceso a la red: modelo de seguridad y recursos compartidos para cuentas locales** diálogo cuadro, cambie el valor a **clásico: usuarios locales autenticados como ellos mismos** y haga clic en el **aplicar**botón.  
  
     ![Opciones de seguridad de directiva de seguridad local](../debugger/media/dbg_err_localsecuritypolicy_securityoptions_networkaccess.png "DBG_ERR_LocalSecurityPolicy_SecurityOptions_NetworkAccess")  
  
## <a name="see-also"></a>Vea también  
 [Errores de depuración remota y sus soluciones](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Depuración remota](../debugger/remote-debugging.md)