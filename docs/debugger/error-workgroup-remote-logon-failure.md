---
title: 'Error: error de inicio de sesión remoto de grupo de trabajo | Microsoft Docs'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d1ee0cfbd021eb7d6a03a791713d187d3c8877c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736261"
---
# <a name="error-workgroup-remote-logon-failure"></a>Error: El grupo de trabajo no ha podido iniciar una sesión remota
Este error reza como sigue:

 Error de inicio de sesión: nombre de usuario desconocido o contraseña incorrecta

 **Causa**

 Este error se produce cuando se está depurando en un equipo de un grupo de trabajo y se intenta conectar con el equipo remoto. Entre las posibles causas se incluyen:

- No existe ninguna cuenta que coincida con el nombre y la contraseña en el equipo remoto.

- Si el equipo de Visual Studio y la máquina remota están en grupos de trabajo, el error se podría producir debido a la configuración predeterminada de la **Directiva de seguridad local** de la máquina remota. La configuración predeterminada de la **Directiva de seguridad local** es **Solo invitado: los usuarios locales se autentican como invitados**. Para depurar en esta configuración, es necesario cambiar la configuración del equipo remoto a **Clásico: usuarios locales autenticados como ellos mismos**.

> [!NOTE]
> Debe ser administrador para llevar a cabo las tareas siguientes.

### <a name="to-open-the-local-security-policy-window"></a>Para abrir la ventana Directiva de seguridad local

1. Inicie el complemento **secpol.msc** en Microsoft Management Console. Escriba secpol.msc en la búsqueda de Windows, el cuadro Ejecutar de Windows o en un símbolo del sistema.

### <a name="to-add-user-rights-assignments"></a>Para agregar asignaciones de derechos de usuario

1. Abra la ventana **Directiva de seguridad local**.

2. Expanda la carpeta **Directivas locales**.

3. Haga clic en **Asignación de derechos de usuario**.

4. En la columna **Directiva**, haga doble clic en **Depurar programas** para ver las asignaciones actuales de la directiva de grupo local en el cuadro de diálogo **Configuración de directiva de seguridad local**.

     ![Derechos de usuario de la Directiva de seguridad local](../debugger/media/dbg_err_localsecuritypolicy_userrightsdebugprograms.png "DBG_ERR_LocalSecurityPolicy_UserRightsDebugPrograms")

5. Para agregar nuevos usuarios, haga clic en el botón **Agregar usuario o grupo**.

### <a name="to-change-the-sharing-and-security-model"></a>Para cambiar el modelo de seguridad y recursos compartidos

1. Abra la ventana **Directiva de seguridad local**.

2. Expanda la carpeta **Directivas locales**.

3. Haga clic en **Opciones de seguridad**.

4. En la columna **Directiva**, haga doble clic en **Acceso de red: modelo de seguridad y recursos compartidos para cuentas locales**.

5. En el cuadro de diálogo **Acceso de red: modelo de seguridad y recursos compartidos para cuentas locales**, cambie el valor a **Clásico: usuarios locales autenticados como ellos mismos** y haga clic en el botón **Aplicar**.

     ![Opciones de seguridad de la Directiva de seguridad local](../debugger/media/dbg_err_localsecuritypolicy_securityoptions_networkaccess.png "DBG_ERR_LocalSecurityPolicy_SecurityOptions_NetworkAccess")

## <a name="see-also"></a>Vea también
- [Errores de la depuración remota y sus soluciones](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Remote Debugging](../debugger/remote-debugging.md)