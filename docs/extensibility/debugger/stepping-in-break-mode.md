---
title: Ejecución paso a paso en modo de interrupción | Microsoft Docs
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
ms.openlocfilehash: 4fff7edc494c763407c65785fe1de0b3fd77d7b2
ms.sourcegitcommit: 8d38d5d2f2b75fc1563952c0d6de0fe43af12766
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/26/2018
ms.locfileid: "39276512"
---
# <a name="stepping-in-break-mode"></a>Ejecución paso a paso en modo de interrupción
La siguiente sección describe el proceso que se produce cuando el depurador está en modo de interrupción y debe recorrer el código:  
  
## <a name="stepping-process"></a>Proceso de ejecución paso a paso  
  
1.  Llame a [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md) con [STEPKIND](../../extensibility/debugger/reference/stepkind.md) y [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) argumentos al ejecutar un paso.  
  
2.  Cuando finalice el paso, enviar un [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) como un evento de detención.  
  
## <a name="see-also"></a>Vea también  
 [Llamar a los eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)