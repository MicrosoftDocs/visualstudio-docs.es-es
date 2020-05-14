---
title: No se puede asociar al proceso | Microsoft Docs
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 22d798d30d09cb509f53d093ae61bb1a02b414ec
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72728876"
---
# <a name="unable-to-attach-to-the-process"></a>No se puede asociar al proceso
No se puede asociar al proceso. Se denegó el acceso al componente del depurador del servidor mientras se conectaba a este equipo.

 Hay dos escenarios comunes que provocan este error:

 **Escenario 1:** el equipo A ejecuta Windows XP. El equipo B ejecuta Windows Server 2003. El Registro del equipo B contiene el siguiente valor DWORD:

 `HKLM\Software\Microsoft\MachineDebugManager\AllowLaunchAsOtherUser=1`

 El Usuario 1 inicia una sesión de Terminal Server (sesión 1) en el equipo B e inicia una aplicación administrada desde esa sesión.

 El Usuario 2, que es el administrador de ambos equipos, ha iniciado sesión en el equipo A. Desde allí, intenta asociarse a una aplicación que se ejecuta en la sesión 1 del equipo B.

 **Escenario 2:** un usuario ha iniciado sesión en dos equipos, A y B, en el mismo grupo de trabajo, con la misma contraseña en ambos equipos. El depurador se está ejecutando en el equipo A e intenta asociarse a una aplicación administrada que se ejecuta en el equipo B. En el equipo A, la opción **Acceso a redes: modelo de seguridad y uso compartido para cuentas locales** está establecida como **Invitado**.

### <a name="to-solve-scenario-1"></a>Para resolver el Escenario 1

- Ejecute el depurador y la aplicación administrada con el mismo nombre de usuario y la misma contraseña.

### <a name="to-solve-scenario-2"></a>Para resolver el Escenario 2

1. En el menú **Inicio**, elija **Panel de control**.

2. En el Panel de control, haga doble clic en **Herramientas administrativas**.

3. En la ventana Herramientas administrativas, haga doble clic en **Directiva de seguridad local**.

4. En la ventana Configuración de seguridad local, seleccione **Directivas locales**.

5. En la columna **Directivas**, haga doble clic en **Acceso a redes: modelo de seguridad y uso compartido para cuentas locales**.

6. En el cuadro de diálogo **Acceso a redes: modelo de seguridad y uso compartido para cuentas locales**, cambie la configuración de seguridad local a **Clásica** y haga clic en **Aceptar**.

    > [!CAUTION]
    > Cambiar el modelo de seguridad a Clásica puede producir un acceso inesperado a archivos compartidos y componentes DCOM. Si realiza este cambio, un usuario remoto puede realizar la autenticación con su cuenta de usuario local en lugar de hacerlo como Invitado. Si la información de un usuario remoto coincide con su nombre de usuario y contraseña, dicho usuario podrá tener acceso a cualquier carpeta u objeto DCOM que haya compartido. Si utiliza este modelo de seguridad, asegúrese de que todas las cuentas de usuario del equipo tengan contraseñas seguras o establezca una isla de red aislada para los equipos depurados y en depuración a fin de evitar el acceso no autorizado.

7. Cierre todas las ventanas.

## <a name="see-also"></a>Vea también
- [Configuración y preparación de la depuración](../debugger/debugger-settings-and-preparation.md)