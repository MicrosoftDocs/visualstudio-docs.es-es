---
title: Ejecución paso a paso en modo de interrupción | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- break mode, stepping
- stepping, in break mode
- debugging [Debugging SDK], stepping in break mode
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1cf10254ec4642bd6dd671124d4a0600794de6fb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="stepping-in-break-mode"></a>Ejecución paso a paso en modo de interrupción
A continuación describe el proceso que se produce cuando el depurador está en modo de interrupción y debe recorrer el código:  
  
## <a name="stepping-process"></a>Proceso de ejecución paso a paso  
  
1.  Llame a [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md) con [STEPKIND](../../extensibility/debugger/reference/stepkind.md) y [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) argumentos para ejecutar un paso.  
  
2.  Cuando haya finalizado el paso, envíe un [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) como un evento de detención.  
  
## <a name="see-also"></a>Vea también  
 [Llamada a eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)