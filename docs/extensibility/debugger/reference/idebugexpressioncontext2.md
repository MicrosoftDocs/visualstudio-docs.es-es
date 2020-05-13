---
title: IDebugExpressionContext2 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionContext2
helpviewer_keywords:
- IDebugExpressionContext2 interface
ms.assetid: 577fdaae-4b2d-4112-9839-ab899535fa6f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 344ae287b3784ceca87fbbab09ad2b2e0a304205
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729642"
---
# <a name="idebugexpressioncontext2"></a>IDebugExpressionContext2
Esta interfaz representa un contexto para la evaluación de expresiones

## <a name="syntax"></a>Sintaxis

```
IDebugExpressionContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El motor de depuración (DE) implementa esta interfaz para representar un contexto en el que se puede evaluar una expresión.

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 Una llamada a [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) devuelve la interfaz this. Esta interfaz solo es accesible cuando el programa que se está depurando se ha pausado y hay un marco de pila disponible.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente `IDebugExpressionContext2`se muestran los métodos de .

|Método|Descripción|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugexpressioncontext2-getname.md)|Recupera el nombre del contexto de evaluación.|
|[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)|Analiza una expresión basada en texto para su evaluación.|

## <a name="remarks"></a>Observaciones
 Un contexto de evaluación se puede considerar como un ámbito para realizar la evaluación de expresiones.

 Cuando un programa se ha detenido, el administrador de depuración de sesión (SDM) obtiene una trama de pila de la DE con una llamada a [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md). A continuación, el SDM llama `IDebugExpressionContext2` a [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) para obtener la interfaz. Esto va seguido de una llamada a [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) para crear un [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) interfaz, que representa la expresión analizada lista para evaluarse.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
