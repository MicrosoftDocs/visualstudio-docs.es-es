---
title: IDebugExceptionEvent2 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugExceptionEvent2
helpviewer_keywords: IDebugExceptionEvent2 interface
ms.assetid: 53d32e59-a84b-4710-833e-c5ab08100516
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: dc6dacbac1092e211ba129417bd4e47aea31b733
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebugexceptionevent2"></a>IDebugExceptionEvent2
El motor de depuración (Alemania) envía esta interfaz para el Administrador de sesión de depuración (SDM) cuando se produce una excepción en el programa que se está ejecutando actualmente.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugExceptionEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 La DE implementa esta interfaz para informes que se ha producido una excepción en el programa que se está depurando. El [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) debe implementar la interfaz en el mismo objeto que esta interfaz. Usa el SDM [QueryInterface](/cpp/atl/queryinterface) para tener acceso a la `IDebugEvent2` interfaz.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 El DIS crean y envía este objeto de evento para informar de una excepción. El evento se envía mediante la [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) función de devolución de llamada proporcionada por el SDM cuando adjunta al programa que se está depurando.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDebugExceptionEvent2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)|Obtiene información detallada sobre la excepción que se desencadenó este evento.|  
|[GetExceptionDescription](../../../extensibility/debugger/reference/idebugexceptionevent2-getexceptiondescription.md)|Obtiene una descripción legible de la excepción que se desencadenó este evento.|  
|[CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)|Determina si se permite o no el motor de depuración (Alemania) es compatible con la opción de pasar esta excepción al programa que se está depurando cuando se reanuda la ejecución.|  
|[PassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)|Especifica si la excepción se debería pasar al programa que se está depurando cuando se reanuda la ejecución, o si se debería descartar la excepción.|  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="remarks"></a>Comentarios  
 Antes de enviar el evento, la DE comprueba para ver si se ha designado una excepción de primera oportunidad o segunda oportunidad a este evento de excepción por una llamada anterior a [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md). Si se ha designado como una excepción de primera oportunidad, la `IDebugExceptionEvent2` evento se envía a la SDM. De lo contrario, ofrece a la DE la aplicación una oportunidad para controlar la excepción. Si no se proporciona ningún controlador de excepción, y si la excepción se ha designado como una excepción de segunda oportunidad, la `IDebugExceptionEvent2` evento se envía a la SDM. En caso contrario, la DE reanuda la ejecución del programa y el sistema operativo o en tiempo de ejecución controla la excepción.  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)