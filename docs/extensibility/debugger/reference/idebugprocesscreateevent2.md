---
title: IDebugProcessCreateEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProcessCreateEvent2
helpviewer_keywords:
- IDebugProcessCreateEvent2
ms.assetid: c660439d-8b23-4dbb-923e-ebb5e1d7edf5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 47d3307bc02af1ca0b202e284790115b771f8ce7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54975262"
---
# <a name="idebugprocesscreateevent2"></a>IDebugProcessCreateEvent2
Esta interfaz se envía cuando se inicia un proceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugProcessCreateEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El motor de depuración (DE) o el proveedor del puerto personalizado implementa esta interfaz para notificar que se ha creado un proceso. El [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaz debe implementarse en el mismo objeto que esta interfaz. Usa el SDM [QueryInterface](/cpp/atl/queryinterface) para tener acceso a la `IDebugEvent2` interfaz.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 La DE o el proveedor del puerto personalizado crea y envía este objeto de evento para notificar la creación de un proceso. La DE envía este evento mediante el [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) función de devolución de llamada suministrada por el SDM cuando está conectado al programa que se está depurando. El proveedor de puerto personalizado envía este evento mediante el [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) interfaz.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces del núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)