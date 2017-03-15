---
title: "Subprocesos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "depurar [SDK de depuración], subprocesos"
  - "subprocesamiento [SDK de depuración]"
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Subprocesos
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

En términos de arquitectura del depurador, **Subproceso**:  
  
-   es la unidad fundamental de cálculo.  Un subproceso ejecuta secuencialmente las instrucciones en el contexto de una sola pila de llamadas, desplácese a partir de un contexto de código a la siguiente.  
  
-   Puede identificarse y el programa que se ejecuta en, y puede ser llamado, suspender, y reanudar.  Un subproceso también pueden mostrar los marcos de pila asociado y, en algunas situaciones, se puede mover a otro marco de pila.  Dado el contexto de un marco de pila, un subproceso puede devolver el subproceso lógico asociado, si existe.  Un subproceso tiene propiedades, como un valor de suspensión, que se puede mostrar en la ventana subprocesos del IDE.  
  
-   Se representa mediante una interfaz de [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) , creada normalmente por un motor de depuración \(DE\) o una máquina virtual como resultado de ejecutar un programa.  
  
## Vea también  
 [Programas](../../extensibility/debugger/programs.md)   
 [Marcos de pila](../../extensibility/debugger/stack-frames.md)   
 [Motor de depuración](../../extensibility/debugger/debug-engine.md)   
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)   
 [Administrador de depuración de sesión](../../extensibility/debugger/session-debug-manager.md)