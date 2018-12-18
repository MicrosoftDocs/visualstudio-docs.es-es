---
title: IDebugPropertyCreateEvent2 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPropertyCreateEvent2
helpviewer_keywords:
- IDebugPropertyCreateEvent2 interface
ms.assetid: 33b3082b-a42e-488a-a1e4-dadf506f922c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cc599480b148e85dd8d70c45282ef52d08b8eabf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31121962"
---
# <a name="idebugpropertycreateevent2"></a>IDebugPropertyCreateEvent2
Esta interfaz se envía por el motor de depuración (Alemania) para el Administrador de sesión de depuración (SDM) cuando crea una propiedad que está asociada a un documento específico.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugPropertyCreateEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 La DE implementa esta interfaz para notificar que se ha creado una propiedad. El [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) debe implementar la interfaz en el mismo objeto que esta interfaz. Usa el SDM [QueryInterface](/cpp/atl/queryinterface) para tener acceso a la `IDebugEvent2` interfaz. Esta interfaz se implementa si la DE ha creado una propiedad asociada con una secuencia de comandos que se ha cargado o creado y si esa secuencia de comandos debe aparecer en el IDE.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 La DE crea y envía este objeto de evento a una propiedad se ha creado el informe. El evento se envía mediante la [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) función de devolución de llamada proporcionada por el SDM cuando se adjunta al programa que se está depurando.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 En la tabla siguiente muestra el método de la `IDebugPropertyCreateEvent2` interfaz.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md)|Obtiene la nueva propiedad.|  
  
## <a name="remarks"></a>Comentarios  
 Si una propiedad tiene un documento o secuencia de comandos asociada con él, la DE puede enviar este evento para el SDM para actualizar la **documentos de Script** ventana con el nombre del documento. El SDM llamará [GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md) con el argumento `guidDocument` para recuperar un `VARIANT` que contiene un [IUnknown](/cpp/atl/iunknown) puntero. El SDM llamará [QueryInterface](/cpp/atl/queryinterface) en este puntero para recuperar el [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interfaz que se utiliza para actualizar la **documentos de Script** ventana.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)