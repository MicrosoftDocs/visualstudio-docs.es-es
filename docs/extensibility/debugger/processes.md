---
title: "Procesos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "depurar [SDK de depuración], procesa"
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Procesos
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

En términos de arquitectura del depurador, **un proceso**:  
  
-   Es un contenedor para un conjunto de software.  Está estrechamente análogo a un proceso de Windows, que es un contenedor para un grupo de subprocesos.  
  
-   puede identificarse por nombre, el identificador, o el identificador físico.  
  
-   Puede mostrar todos los programas en ejecución \(y sus subprocesos\).  
  
-   Puede describirse, el puerto que se ejecuta en, y el equipo que lo contiene.  
  
-   Puede crear uno o más programas, finalizar los programas cualquiera de los que crea, o hacer un programa deje.  
  
-   Se representa mediante una interfaz de [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) , que se crea cuando se inicia el proceso.  Un proceso es iniciadas por el administrador o [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)\(SDM\) de depuración de la sesión.  
  
 El paquete de depuración se puede adjuntar un motor de depuración \(DE\) a un proceso llamando a [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md).  Esto significa que el OF adjunta a todos los programas posibles que se ejecutan en el proceso que puede controlar.  Por ejemplo, si Common Language Runtime OF se asocia a un proceso, asocia sólo a los programas que se están ejecutando código administrado.  
  
## Vea también  
 [Programas](../../extensibility/debugger/programs.md)   
 [Subprocesos](../../extensibility/debugger/threads.md)   
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)   
 [Depurar paquete](../../extensibility/debugger/debug-package.md)   
 [Motor de depuración](../../extensibility/debugger/debug-engine.md)   
 [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)   
 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md)