---
title: IDebugStackFrame3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugStackFrame3
helpviewer_keywords:
- IDebugStackFrame3 interface
ms.assetid: 39af2f57-0a01-42b8-b093-b7fbc61e2909
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 376807a2963e93b3713d85b2d166c741671079bf
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53932777"
---
# <a name="idebugstackframe3"></a>IDebugStackFrame3
Esta interfaz extiende [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) para controlar las excepciones interceptadas.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugStackFrame3 : IDebugStackFrame2  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El motor de depuración (DE) implementa esta interfaz en el mismo objeto que implementa el [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) interfaz para admitir excepciones interceptadas.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Llame a [QueryInterface](/cpp/atl/queryinterface) en un `IDebugStackFrame2` interfaz para obtener esta interfaz.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 Además de los métodos heredados de [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md), `IDebugStackFrame3` expone los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)|Controla una excepción para el marco de pila actual antes de cualquier control de excepciones.|  
|[GetUnwindCodeContext](../../../extensibility/debugger/reference/idebugstackframe3-getunwindcodecontext.md)|Devuelve un contexto de código si se produce un desenredo de pila.|  
  
## <a name="remarks"></a>Comentarios  
 Una excepción interceptada significa que un depurador puede procesar una excepción antes de llamar a las rutinas de control de excepciones normales por el tiempo de ejecución. Interceptar esencialmente una excepción, se hace que el tiempo de ejecución fingir que hay presente incluso cuando no hay un controlador de excepciones.  
  
 [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) se llama durante todos los eventos de devolución de llamada de excepción normal (la única excepción a esto es si está depurando código de modo mixto (administrado y código no administrado), en cuyo caso no se puede interceptar la excepción durante la devolución de llamada de oportunidad como último). Si no implementa la DE `IDebugStackFrame3`, o la DE devuelve un error de IDebugStackFrame3::`InterceptCurrentException` (como `E_NOTIMPL`), a continuación, el depurador va a controlar la excepción con normalidad.  
  
 Al interceptar una excepción, el depurador puede permitir al usuario realizar cambios en el estado del programa que se está depurando y, a continuación, reanudar la ejecución en el punto donde se produjo la excepción.  
  
> [!NOTE]
>  Interceptar las excepciones pueden solo en código administrado, es decir, en un programa que se ejecuta en Common Language Runtime (CLR).  
  
 Un motor de depuración indica que es compatible con las excepciones interceptadas estableciendo "metricExceptions" en un valor de 1 en tiempo de ejecución mediante el uso de la `SetMetric` función. Para obtener más información, consulte [aplicaciones auxiliares de SDK para depuración](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces del núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [Asistentes de SDK para la depuración](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)