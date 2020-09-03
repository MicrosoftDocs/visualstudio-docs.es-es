---
title: Paso a paso en modo de interrupción | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode, stepping
- stepping, in break mode
- debugging [Debugging SDK], stepping in break mode
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3161fc1c1ec8b44d96b3793198ac630ba2e32d67
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712854"
---
# <a name="stepping-in-break-mode"></a>Ejecución paso a paso en modo de interrupción
En la siguiente sección se describe el proceso que se produce cuando el depurador está en modo de interrupción y debe recorrer el código:

## <a name="stepping-process"></a>Proceso de ejecución paso a paso

1. Llame a [IDebugProgram2:: Step](../../extensibility/debugger/reference/idebugprogram2-step.md) con los argumentos [STEPKIND](../../extensibility/debugger/reference/stepkind.md) y [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) para ejecutar un paso.

2. Cuando finalice el paso, envíe un [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) como evento de detención.

## <a name="see-also"></a>Vea también
- [Llamar a eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)
