---
title: IDebugExpressionContext2 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugExpressionContext2
helpviewer_keywords:
- IDebugExpressionContext2 interface
ms.assetid: 577fdaae-4b2d-4112-9839-ab899535fa6f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4da916f67611f594b14a41cbb2838f4565eb7fe3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugexpressioncontext2"></a>IDebugExpressionContext2
Esta interfaz representa un contexto para la evaluación de expresión  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugExpressionContext2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El motor de depuración (Alemania) implementa esta interfaz para representar un contexto en el que se puede evaluar una expresión.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Una llamada a [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) devuelve esta interfaz. Esta interfaz es accesible sólo cuando se ha detenido el programa que se está depurando y un marco de pila está disponible.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDebugExpressionContext2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetName](../../../extensibility/debugger/reference/idebugexpressioncontext2-getname.md)|Recupera el nombre del contexto de evaluación.|  
|[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)|Analiza una expresión basada en texto para su evaluación.|  
  
## <a name="remarks"></a>Comentarios  
 Un contexto de evaluación puede considerarse como un ámbito para llevar a cabo la evaluación de expresiones.  
  
 Cuando un programa se ha detenido, el Administrador de sesión de depuración (SDM) Obtiene un marco de pila de la DE con una llamada a [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md). El SDM, a continuación, llama [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) para obtener el `IDebugExpressionContext2` interfaz. Esto es seguido por una llamada a [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) para crear un [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) interfaz que representa la expresión analizada lista para ser evaluada.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)   
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)