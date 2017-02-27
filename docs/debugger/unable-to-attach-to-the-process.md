---
title: "No se puede asociar al proceso | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.remote.unable2attach"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 0468de6c-3ff1-4979-a8c6-8afb53f37547
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# No se puede asociar al proceso
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

No se puede asociar al proceso.Se denegó el acceso al componente del depurador del servidor mientras se conectaba a este equipo.  
  
 Hay dos escenarios comunes que provocan este error:  
  
 **Escenario 1:** el equipo A ejecuta Windows XP.  El equipo B ejecuta Windows Server 2003.  El Registro del equipo B contiene el siguiente valor DWORD:  
  
 `HKLM\Software\Microsoft\MachineDebugManager\AllowLaunchAsOtherUser=1`  
  
 El Usuario 1 inicia una sesión de Terminal Server \(sesión 1\) en el equipo B e inicia una aplicación administrada desde esa sesión.  
  
 El Usuario 2, que es el administrador de ambos equipos, inició una sesión en el equipo A.  Desde allí, intenta adjuntarse a una aplicación que se ejecuta en la sesión 1 del equipo B.  
  
 **Escenario 2:** un usuario ha iniciado sesión en dos equipos, A y B, en el mismo grupo de trabajo, con la misma contraseña en ambos equipos.  El depurador se está ejecutando en el equipo A e intenta adjuntarse a una aplicación administrada que se ejecuta en el equipo B.  En el equipo A, la opción **Acceso de red: modelo de seguridad y recursos compartidos para cuentas locales** está establecida como **Invitado**.  
  
### Para resolver el Escenario 1  
  
-   Ejecute el depurador y la aplicación administrada con el mismo nombre de usuario y la misma contraseña.  
  
### Para resolver el Escenario 2  
  
1.  En el menú **Inicio**, elija **Panel de control**.  
  
2.  En el Panel de control, haga doble clic en **Herramientas administrativas**.  
  
3.  En la ventana Herramientas administrativas, haga doble clic en **Directiva de seguridad local**.  
  
4.  En la ventana Configuración de seguridad local, seleccione **Directivas locales**.  
  
5.  En la columna **Directivas**, haga doble clic en **Acceso de red: modelo de seguridad y recursos compartidos para cuentas locales**.  
  
6.  En el cuadro de diálogo **Acceso de red: modelo de seguridad y recursos compartidos para cuentas locales**, cambie la configuración de seguridad local a **Clásica** y haga clic en **Aceptar**.  
  
    > [!CAUTION]
    >  Cambiar el modelo de seguridad a Clásica puede producir un acceso inesperado a archivos compartidos y componentes DCOM.  Si realiza este cambio, un usuario remoto puede realizar la autenticación con su cuenta de usuario local en lugar de hacerlo como Invitado.  Si la información de un usuario remoto coincide con su nombre de usuario y contraseña, dicho usuario podrá tener acceso a cualquier carpeta u objeto DCOM que haya compartido.  Si utiliza este modelo de seguridad, asegúrese de que todas las cuentas de usuario del equipo tengan contraseñas seguras o establezca una isla de red aislada para los equipos depurados y en depuración a fin de evitar el acceso no autorizado.  
  
7.  Cierre todas las ventanas.  
  
## Vea también  
 [Preparación y configuración de la depuración](../debugger/debugger-settings-and-preparation.md)