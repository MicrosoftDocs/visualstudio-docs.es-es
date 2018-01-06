---
title: IDebugProgramDestroyEvent2 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgramDestroyEvent2
helpviewer_keywords: IDebugProgramDestroyEvent2
ms.assetid: ddf127ca-c4a5-4071-90ca-68faf2f57dbd
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8cae0510e464d5aefcb5911387635be2dfb44987
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogramdestroyevent2"></a>IDebugProgramDestroyEvent2
Esta interfaz se envía por el motor de depuración (Alemania) para el Administrador de sesión de depuración (SDM) cuando un programa se ejecute hasta completarse.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugProgramDestroyEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El proveedor de puerto personalizado o la DE implementa esta interfaz para el informe de que un programa ha terminado y ya no está disponible para la depuración. El [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) debe implementar la interfaz en el mismo objeto que esta interfaz. Usa el SDM [QueryInterface](/cpp/atl/queryinterface) para tener acceso a la `IDebugEvent2` interfaz.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 El proveedor de puerto personalizado o la DE crea y envía este objeto de evento para notificar la finalización de un programa. La DE envía este evento mediante el [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) función de devolución de llamada proporcionada por el SDM cuando adjunta al programa que se está depurando. El proveedor de puerto personalizado envía este evento mediante el [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) interfaz.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 En la tabla siguiente muestra el método de `IDebugProgramDestroyEvent2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetExitCode](../../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md)|Obtiene el código de salida del programa.|  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)