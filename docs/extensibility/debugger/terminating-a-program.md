---
title: Finalización de un programa | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debugging [Debugging SDK], terminating a program
ms.assetid: eedda0a3-5e05-44fe-841d-a2f4866ac72d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 985b20fe75f8ceee3d434ac681b437c51baf85e8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712522"
---
# <a name="terminating-a-program"></a>Finalización de un programa
En la siguiente sección se describe la terminación de un único programa con un subproceso.

## <a name="termination-process"></a>Proceso de finalización

1. El DE envía un [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) con un [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md)válido.

2. El DE envía un [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) con un [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)válido.

   El IDE entra en el modo de diseño. El motor de depuración o el entorno de tiempo de ejecución llama a [IDebugPortNotify2:: RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) para quitar el programa del puerto.

## <a name="see-also"></a>Vea también
- [Llamar a eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)
