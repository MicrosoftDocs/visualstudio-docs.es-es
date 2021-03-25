---
title: Paso a paso en modo de interrupción | Microsoft Docs
description: Obtenga información sobre el proceso que se produce cuando el depurador está en modo de interrupción. Después, el depurador debe recorrer el código.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode, stepping
- stepping, in break mode
- debugging [Debugging SDK], stepping in break mode
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0ed11d05e4351ac6ba76bc9aa10531a8a96ddf23
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105075411"
---
# <a name="stepping-in-break-mode"></a>Ejecución paso a paso en modo de interrupción
En la siguiente sección se describe el proceso que se produce cuando el depurador está en modo de interrupción y debe recorrer el código:

## <a name="stepping-process"></a>Proceso de ejecución paso a paso

1. Llame a [IDebugProgram2:: Step](../../extensibility/debugger/reference/idebugprogram2-step.md) con los argumentos [STEPKIND](../../extensibility/debugger/reference/stepkind.md) y [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) para ejecutar un paso.

2. Cuando finalice el paso, envíe un [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) como evento de detención.

## <a name="see-also"></a>Consulte también
- [Llamar a eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)
