---
title: Evaluación de la pila de llamadas | Microsoft Docs
description: Obtenga información sobre el método EnumFrameInfo y cómo implementarlo para ver los marcos de pila de la pila de llamadas durante el modo de interrupción.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], call stack evaluation
- call stacks, evaluation
ms.assetid: 373d6b49-0459-4cce-816e-05745a44fe49
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 223b1fff75c8fefdfed5bce5765d82fc5309738d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99930738"
---
# <a name="call-stack-evaluation"></a>Evaluación de la pila de llamadas
Para ver los marcos de pila de la pila de llamadas durante el modo de interrupción, debe implementar el método [EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) .

## <a name="methods-for-evaluation"></a>Métodos de evaluación
 Para un motor de depuración simple (DE), puede haber un solo marco de pila. Para examinar el marco de pila durante el modo de interrupción, debe implementar los métodos siguientes de [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md).

|Método|Descripción|
|------------|-----------------|
|[GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Obtiene el contexto de código para un marco de pila. El contexto de código representa el puntero de instrucción actual en un marco de pila.|
|[GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Obtiene el contexto del documento para un marco de pila. El contexto del documento representa la ubicación actual en el código fuente de un marco de pila. Necesario para ver el código fuente cuando se detiene en un programa.|

 Estos métodos requieren la implementación de varias interfaces y métodos relacionados con el contexto. Por lo tanto, debe implementar el método [GetDocumentContext](../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) y los siguientes métodos de [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md).

|Método|Descripción|
|------------|-----------------|
|[GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Obtiene el intervalo de instrucciones de archivo de un contexto de documento.|

 Para enumerar los contextos de código, debe implementar todos los métodos de [IEnumDebugCodeContexts2](../../extensibility/debugger/reference/ienumdebugcodecontexts2.md).

## <a name="see-also"></a>Vea también
- [Control de ejecución y evaluación del estado](../../extensibility/debugger/execution-control-and-state-evaluation.md)
