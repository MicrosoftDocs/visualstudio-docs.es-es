---
title: IDebugInterceptExceptionCompleteEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugInterceptExceptionCompleteEvent2
helpviewer_keywords:
- IDebugInterceptExceptionCompleteEvent2
ms.assetid: 8ebc256b-5428-4ed6-a505-6aedc8242b8e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0a54ea7c9745eedf2fe86aed2df29a380447e154
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54932784"
---
# <a name="idebuginterceptexceptioncompleteevent2"></a>IDebugInterceptExceptionCompleteEvent2
Esta interfaz se envía por el motor de depuración (DE) el Administrador de depuración de la sesión (SDM) cuando se haya completado la DE la administración de un evento interceptado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugInterceptExceptionCompleteEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 La DE implementa esta interfaz para notificar que se ha completado el procesamiento de una excepción interceptada. El [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaz debe implementarse en el mismo objeto que esta interfaz. Usa el SDM [QueryInterface](/cpp/atl/queryinterface) para tener acceso a la `IDebugEvent2` interfaz.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 La DE crea y envía este objeto de evento para notificar la finalización de una excepción interceptada. El evento se envía mediante la [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) función de devolución de llamada que proporciona el SDM cuando adjunta al programa que se está depurando.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 El `IDebugInterceptExceptionCompleteEvent2` interfaz implementa los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetInterceptCookie](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2-getinterceptcookie.md)|Devuelve el valor único asociado con la excepción controlada.|  
  
## <a name="remarks"></a>Comentarios  
 Este evento se enviarán por [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) cuando ese método se haya completado correctamente controla una excepción interceptada.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces del núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)