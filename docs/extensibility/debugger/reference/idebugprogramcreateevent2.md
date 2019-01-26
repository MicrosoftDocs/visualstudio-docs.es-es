---
title: IDebugProgramCreateEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgramCreateEvent2
helpviewer_keywords:
- IDebugProgramCreateEvent2 interface
ms.assetid: b19a7934-6179-4a68-9075-bd7dcd640b05
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0f72b2fac6e8265ffebeb751c6118003f4c75bcd
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54962789"
---
# <a name="idebugprogramcreateevent2"></a>IDebugProgramCreateEvent2
Esta interfaz se envía por el motor de depuración (DE) el Administrador de depuración de la sesión (SDM) cuando un programa se asocia a.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugProgramCreateEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 La DE o el proveedor del puerto personalizado implementa esta interfaz para notificar que se creó un programa, normalmente en el momento en que el programa está asociado a. El [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaz debe implementarse en el mismo objeto que esta interfaz. Usa el SDM el `QueryInterface` método para acceder a la `IDebugEvent2` interfaz.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 La DE o el proveedor del puerto personalizado crea y envía este objeto de evento para notificar la creación de un programa. La DE envía este evento mediante el [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) función de devolución de llamada que proporciona el SDM cuando adjunta al programa que se está depurando. El proveedor de puerto personalizado envía este evento mediante el [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) interfaz.  
  
## <a name="remarks"></a>Comentarios  
 El DE o el proveedor de puerto personalizado publica un nuevo [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) interfaz mediante una llamada a [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md).  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces del núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)