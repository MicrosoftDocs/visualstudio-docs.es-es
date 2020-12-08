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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 80273bf470a3ed0c342e781085de6e991508451c
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845198"
---
# <a name="stepping-in-break-mode"></a>Ejecución paso a paso en modo de interrupción
En la siguiente sección se describe el proceso que se produce cuando el depurador está en modo de interrupción y debe recorrer el código:

## <a name="stepping-process"></a>Proceso de ejecución paso a paso

1. Llame a [IDebugProgram2:: Step](../../extensibility/debugger/reference/idebugprogram2-step.md) con los argumentos [STEPKIND](../../extensibility/debugger/reference/stepkind.md) y [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) para ejecutar un paso.

2. Cuando finalice el paso, envíe un [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) como evento de detención.

## <a name="see-also"></a>Vea también
- [Llamar a eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)
