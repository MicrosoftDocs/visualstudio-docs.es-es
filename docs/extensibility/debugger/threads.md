---
title: Subprocesos | Microsoft Docs
description: En este artículo se describe la definición y el rol de un subproceso en la arquitectura del depurador en Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dc745a4361c0935896048bbf72a4084f007ecf7b
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905740"
---
# <a name="threads"></a>Subprocesos
En la arquitectura del depurador, un *subproceso*:

- Es la unidad fundamental de cálculo. Un subproceso ejecuta secuencialmente sus instrucciones en el contexto de una sola pila de llamadas, pasando de un contexto de código a otro.

- Puede identificarse a sí mismo y al programa en el que se ejecuta. Los subprocesos se pueden denominar, suspender y reanudar. Un subproceso también puede enumerar sus marcos de pila asociados y, en algunas condiciones, se puede mover a otro marco de pila. Dado el contexto de un marco de pila, un subproceso puede devolver su subproceso lógico asociado, si lo hay. Un subproceso tiene propiedades, como un recuento de suspensión, que se pueden mostrar en la **ventana Subprocesos** del IDE.

- Se representa mediante una [interfaz IDebugThread2,](../../extensibility/debugger/reference/idebugthread2.md) que normalmente se crea mediante un motor de depuración (DE) o una máquina virtual como consecuencia de la ejecución de un programa.

## <a name="see-also"></a>Consulta también
- [Programs](../../extensibility/debugger/programs.md)
- [Marcos de pila](../../extensibility/debugger/stack-frames.md)
- [Motor de depuración](../../extensibility/debugger/debug-engine.md)
- [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)
- [Administrador de depuración de sesión](../../extensibility/debugger/session-debug-manager.md)
