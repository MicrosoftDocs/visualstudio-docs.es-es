---
title: Finalización de un programa | Microsoft Docs
description: En este artículo se describe cómo el IDE utiliza el motor de depuración para finalizar un único programa con un solo subproceso.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debugging [Debugging SDK], terminating a program
ms.assetid: eedda0a3-5e05-44fe-841d-a2f4866ac72d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0f44cb287945576d361d0318eaeafa42de99871d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895913"
---
# <a name="terminating-a-program"></a>Finalización de un programa
En la siguiente sección se describe la terminación de un único programa con un subproceso.

## <a name="termination-process"></a>Proceso de finalización

1. El DE envía un [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) con un [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md)válido.

2. El DE envía un [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) con un [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)válido.

   El IDE entra en el modo de diseño. El motor de depuración o el entorno de tiempo de ejecución llama a [IDebugPortNotify2:: RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) para quitar el programa del puerto.

## <a name="see-also"></a>Vea también
- [Llamar a eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)
