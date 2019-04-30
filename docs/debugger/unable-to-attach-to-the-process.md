---
title: No se puede asociar al proceso | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.remote.unable2attach
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 0468de6c-3ff1-4979-a8c6-8afb53f37547
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ee917e10809f07ac7c93f924711b0ed42c28135b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63407745"
---
# <a name="unable-to-attach-to-the-process"></a>No se puede asociar al proceso
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

No se puede asociar al proceso. Se denegó el acceso al componente del depurador del servidor mientras se conectaba a este equipo.  
  
 Hay dos escenarios comunes que provocan este error:  
  
 **Escenario 1:** Un equipo se está ejecutando Windows XP. El equipo B ejecuta Windows Server 2003. El Registro del equipo B contiene el siguiente valor DWORD:  
  
 `HKLM\Software\Microsoft\MachineDebugManager\AllowLaunchAsOtherUser=1`  
  
 El Usuario 1 inicia una sesión de Terminal Server (sesión 1) en el equipo B e inicia una aplicación administrada desde esa sesión.  
  
 El usuario 2, que es administrador en ambos equipos, inició sesión en el equipo A. Desde allí, intenta conectar a una aplicación que se ejecuta en la sesión 1 del equipo B.  
  
 **Escenario 2:** Un usuario ha iniciado sesión en dos equipos, A y B, en el mismo grupo de trabajo, con la misma contraseña en ambos equipos. El depurador se está ejecutando en la máquina e intenta asociarse a una aplicación administrada que se ejecuta en el equipo B. **acceso de red: Modelo de seguridad y recursos compartidos para cuentas locales** establecido en **invitado**.  
  
### <a name="to-solve-scenario-1"></a>Para resolver el Escenario 1  
  
- Ejecute el depurador y la aplicación administrada con el mismo nombre de usuario y la misma contraseña.  
  
### <a name="to-solve-scenario-2"></a>Para resolver el Escenario 2  
  
1. En el menú **Inicio**, elija **Panel de control**.  
  
2. En el Panel de control, haga doble clic en **Herramientas administrativas**.  
  
3. En la ventana Herramientas administrativas, haga doble clic en **Directiva de seguridad local**.  
  
4. En la ventana Configuración de seguridad local, seleccione **Directivas locales**.  
  
5. En el **directivas** columna, haga doble clic en **acceso de red: Modelo de seguridad y recursos compartidos para cuentas locales**.  
  
6. En el **acceso de red: Modelo de seguridad y recursos compartidos para cuentas locales** diálogo cuadro, cambie la configuración de seguridad local para **clásico**y haga clic en **Aceptar**.  
  
    > [!CAUTION]
    >   Cambiar el modelo de seguridad a Clásica puede producir un acceso inesperado a archivos compartidos y componentes DCOM. Si realiza este cambio, un usuario remoto puede realizar la autenticación con su cuenta de usuario local en lugar de hacerlo como Invitado. Si la información de un usuario remoto coincide con su nombre de usuario y contraseña, dicho usuario podrá tener acceso a cualquier carpeta u objeto DCOM que haya compartido. Si utiliza este modelo de seguridad, asegúrese de que todas las cuentas de usuario del equipo tengan contraseñas seguras o establezca una isla de red aislada para los equipos depurados y en depuración a fin de evitar el acceso no autorizado.  
  
7. Cierre todas las ventanas.  
  
## <a name="see-also"></a>Vea también  
 [Configuración y preparación de la depuración](../debugger/debugger-settings-and-preparation.md)
