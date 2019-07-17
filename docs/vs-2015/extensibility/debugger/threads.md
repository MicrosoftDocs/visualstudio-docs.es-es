---
title: Subprocesos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 028ad25495ba01d9763c8bec3bbb9c4480d72ff8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68185354"
---
# <a name="threads"></a>Subprocesos
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En cuanto a la arquitectura de depurador, un **subproceso**:  
  
- Es la unidad fundamental del cálculo. Un subproceso ejecuta secuencialmente las instrucciones dentro del contexto de una misma pila de llamadas, mover desde el contexto de un código a la siguiente.  
  
- Puede identificar a sí mismo y el programa se está ejecutando y puede denominado, suspender y reanudar. Un subproceso también puede enumerar sus marcos de pila asociado y, en determinadas condiciones, se puede mover a otro marco de pila. Dado el contexto de un marco de pila, un subproceso puede devolver su subproceso lógico asociado, si existe. Un subproceso tiene propiedades, como un recuento de suspensión, que se pueden mostrar en la ventana de subprocesos del IDE.  
  
- Se representa mediante un [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) interfaz, suelen ser creado por un motor de depuración (DE) o una máquina virtual como consecuencia de ejecutar un programa.  
  
## <a name="see-also"></a>Vea también  
 [Programas](../../extensibility/debugger/programs.md)   
 [Marcos de pila](../../extensibility/debugger/stack-frames.md)   
 [Motor de depuración](../../extensibility/debugger/debug-engine.md)   
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)   
 [Administrador de depuración de sesión](../../extensibility/debugger/session-debug-manager.md)
