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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: db67e0a391f40fc17a80e616e10aa46a600337a4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057863"
---
# <a name="terminating-a-program"></a>Finalización de un programa
En la siguiente sección se describe la terminación de un único programa con un subproceso.

## <a name="termination-process"></a>Proceso de finalización

1. El DE envía un [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) con un [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md)válido.

2. El DE envía un [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) con un [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)válido.

   El IDE entra en el modo de diseño. El motor de depuración o el entorno de tiempo de ejecución llama a [IDebugPortNotify2:: RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) para quitar el programa del puerto.

## <a name="see-also"></a>Consulte también
- [Llamar a eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)
