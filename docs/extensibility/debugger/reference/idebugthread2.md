---
title: IDebugThread2 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugThread2
helpviewer_keywords:
- IDebugThread2 interface
ms.assetid: 221b4b1b-4a26-466e-bc29-5eff800fab13
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d93744e55a3e516a131e772fd2df09da5ec23168
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31121331"
---
# <a name="idebugthread2"></a>IDebugThread2
Esta interfaz representa un subproceso que se ejecuta en un programa.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugThread2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El motor de depuración (Alemania) implementa esta interfaz para representar un subproceso de ejecución en un único programa.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Llame a [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md) para obtener esta interfaz que representa el subproceso actualmente activo.  
  
 Esta interfaz también se utiliza para crear una solicitud de punto de interrupción (vea [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)).  
  
 Esta interfaz también se devuelve al resolver un punto de interrupción enlazado o error (vea [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) y [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)).  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDebugThread2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)|Recupera una lista de los marcos de pila para este subproceso.|  
|[GetName](../../../extensibility/debugger/reference/idebugthread2-getname.md)|Obtiene el nombre del subproceso.|  
|[SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)|Establece el nombre del subproceso.|  
|[GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)|Obtiene el programa en que se ejecuta un subproceso.|  
|[CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)|Determina si se puede establecer la siguiente instrucción en el contexto del marco y el código de pila determinado.|  
|[SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)|Establece la siguiente instrucción en el contexto de marco y el código de pila determinado.|  
|[GetThreadId](../../../extensibility/debugger/reference/idebugthread2-getthreadid.md)|Obtiene el identificador de subproceso del sistema.|  
|[Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md)|Suspende un subproceso.|  
|[Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)|Reanuda un subproceso.|  
|[GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)|Obtiene las propiedades que describen un subproceso.|  
|[GetLogicalThread](../../../extensibility/debugger/reference/idebugthread2-getlogicalthread.md)|Obtiene el subproceso lógico asociado a este subproceso físico.|  
  
## <a name="remarks"></a>Comentarios  
 Dado que un único subproceso físico se puede ejecutar en varios programas, más de un `IDebugThread2` de más de un programa puede representar el mismo subproceso físico.  
  
 Cuando se produce un punto de interrupción o una excepción, se envía un evento mediante una llamada a [eventos](../../../extensibility/debugger/reference/idebugeventcallback2-event.md). Uno de los argumentos de este método es un `IDebugThread2` interfaz que representa el subproceso actual. [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) se usa para obtener la [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) interfaz para el marco de pila actual.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)