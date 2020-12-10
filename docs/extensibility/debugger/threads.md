---
title: Subprocesos | Microsoft Docs
description: En este artículo se describe la definición y el rol de un subproceso en la arquitectura del depurador de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b259ffd7814b42145489ee5990cee6da891a9d10
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2020
ms.locfileid: "96995959"
---
# <a name="threads"></a>Subprocesos
En la arquitectura del depurador, un *subproceso*:

- Es la unidad fundamental de cálculo. Un subproceso ejecuta secuencialmente sus instrucciones en el contexto de una sola pila de llamadas, pasando de un contexto de código al siguiente.

- Puede identificarse y el programa en el que se está ejecutando. Los subprocesos se pueden denominar, suspender y reanudar. Un subproceso también puede enumerar sus marcos de pila asociados y, en algunas condiciones, se puede desplace a otro marco de pila. Dado el contexto de un marco de pila, un subproceso puede devolver su subproceso lógico asociado, si existe. Un subproceso tiene propiedades, como un recuento de suspensión, que se pueden mostrar en la ventana **subprocesos** del IDE.

- Se representa mediante una interfaz [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) , creada normalmente por un motor de depuración (de) o una máquina virtual como consecuencia de la ejecución de un programa.

## <a name="see-also"></a>Consulte también
- [Programs](../../extensibility/debugger/programs.md)
- [Marcos de pila](../../extensibility/debugger/stack-frames.md)
- [Motor de depuración](../../extensibility/debugger/debug-engine.md)
- [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)
- [Administrador de depuración de sesión](../../extensibility/debugger/session-debug-manager.md)
