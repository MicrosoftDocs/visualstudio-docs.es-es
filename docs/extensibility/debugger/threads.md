---
title: Subprocesos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a2754d3b1b15771f876855e7ca7d1dc510748308
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="threads"></a>Subprocesos
En cuanto a la arquitectura del depurador, una **subproceso**:  
  
-   Es la unidad fundamental de cálculo. Un subproceso ejecuta secuencialmente las instrucciones dentro del contexto de una pila de llamadas solo, mover desde el contexto de un código a la siguiente.  
  
-   Puede identificar propio y el programa se está ejecutando y puede denominado, suspender y reanudar. Un subproceso también puede enumerar sus marcos de pila asociado y, en determinadas condiciones, se puede mover a otro marco de pila. Dado el contexto de un marco de pila, un subproceso puede devolver un subproceso lógico asociado, si lo hay. Un subproceso tiene propiedades, como un recuento de suspensión, que se pueden mostrar en la ventana de subprocesos del IDE.  
  
-   Se representa mediante un [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) interfaz, suelen ser creado por un motor de depuración (Alemania) o la máquina virtual como consecuencia de ejecutar un programa.  
  
## <a name="see-also"></a>Vea también  
 [Programas](../../extensibility/debugger/programs.md)   
 [Marcos de pila](../../extensibility/debugger/stack-frames.md)   
 [Motor de depuración](../../extensibility/debugger/debug-engine.md)   
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)   
 [Administrador de depuración de sesión](../../extensibility/debugger/session-debug-manager.md)