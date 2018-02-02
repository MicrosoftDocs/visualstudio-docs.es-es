---
title: No se puede adjuntar al proceso | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vs.debug.remote.unable2attach
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 15acb250c561cb1c7d414784f355a9239ead53ef
ms.sourcegitcommit: d6327b978661c0a745bf4b59f32d8171607803a3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2018
---
# <a name="unable-to-attach-to-the-process"></a>No se puede asociar al proceso
No se puede asociar al proceso. Se denegó el acceso al componente del depurador del servidor mientras se conectaba a este equipo.  
  
 Hay dos escenarios comunes que provocan este error:  
  
 **Escenario 1:** equipo A ejecuta Windows XP. El equipo B ejecuta Windows Server 2003. El Registro del equipo B contiene el siguiente valor DWORD:  
  
 `HKLM\Software\Microsoft\MachineDebugManager\AllowLaunchAsOtherUser=1`  
  
 El Usuario 1 inicia una sesión de Terminal Server (sesión 1) en el equipo B e inicia una aplicación administrada desde esa sesión.  
  
 Usuario 2, que es administrador en ambos equipos, se registra en el equipo A. Desde allí, intenta asociar a una aplicación que se ejecuta en la sesión 1 del equipo B.  
  
 **Escenario 2:** un usuario ha iniciado sesión en dos equipos, A y B, en el mismo grupo de trabajo, con la misma contraseña en ambos equipos. El depurador se ejecuta en el equipo A e intenta asociar a una aplicación administrada que se ejecuta en el equipo B. **acceso a la red: modelo de seguridad y recursos compartidos para cuentas locales** establecido en **invitado**.  
  
### <a name="to-solve-scenario-1"></a>Para resolver el Escenario 1  
  
-   Ejecute el depurador y la aplicación administrada con el mismo nombre de usuario y la misma contraseña.  
  
### <a name="to-solve-scenario-2"></a>Para resolver el escenario 2  
  
1.  Desde el **iniciar** menú, elija **el Panel de Control**.  
  
2.  En el Panel de Control, haga doble clic en **herramientas administrativas**.  
  
3.  En la ventana Herramientas administrativas, haga doble clic en **directiva de seguridad Local**.  
  
4.  En la ventana Directiva de seguridad Local, seleccione **directivas locales**.  
  
5.  En el **directivas** columna, haga doble clic en **acceso a la red: modelo de seguridad y recursos compartidos para cuentas locales**.  
  
6.  En el **acceso a la red: modelo de seguridad y recursos compartidos para cuentas locales** diálogo cuadro, cambie la configuración de seguridad local para **clásico**y haga clic en **Aceptar**.  
  
    > [!CAUTION]
    >    Cambiar el modelo de seguridad a Clásica puede producir un acceso inesperado a archivos compartidos y componentes DCOM. Si realiza este cambio, un usuario remoto puede realizar la autenticación con su cuenta de usuario local en lugar de hacerlo como Invitado. Si la información de un usuario remoto coincide con su nombre de usuario y contraseña, dicho usuario podrá tener acceso a cualquier carpeta u objeto DCOM que haya compartido. Si utiliza este modelo de seguridad, asegúrese de que todas las cuentas de usuario del equipo tengan contraseñas seguras o establezca una isla de red aislada para los equipos depurados y en depuración a fin de evitar el acceso no autorizado.  
  
7.  Cierre todas las ventanas.  
  
## <a name="see-also"></a>Vea también  
 [Configuración y preparación de la depuración](../debugger/debugger-settings-and-preparation.md)