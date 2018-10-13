---
title: IDebugPropertyCreateEvent2 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugPropertyCreateEvent2
helpviewer_keywords:
- IDebugPropertyCreateEvent2 interface
ms.assetid: 33b3082b-a42e-488a-a1e4-dadf506f922c
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8efe7a75bdeed6016571a9b6e008eafe7fd0fbb2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49208941"
---
# <a name="idebugpropertycreateevent2"></a>IDebugPropertyCreateEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Esta interfaz se envía por el motor de depuración (DE) el Administrador de depuración de la sesión (SDM) cuando crea una propiedad que está asociada a un documento específico.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugPropertyCreateEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 La DE implementa esta interfaz para notificar que una propiedad se ha creado. El [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaz debe implementarse en el mismo objeto que esta interfaz. Usa el SDM [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) para tener acceso a la `IDebugEvent2` interfaz. Esta interfaz se implementa si la DE ha creado una propiedad asociada con una secuencia de comandos que se ha cargado o creado y si esa secuencia de comandos debe aparecer en el IDE.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 La DE crea y envía este objeto de evento a una propiedad se ha creado el informe. El evento se envía mediante la [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) función de devolución de llamada suministrada por el SDM cuando está conectado al programa que se está depurando.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 En la tabla siguiente se muestra el método de la `IDebugPropertyCreateEvent2` interfaz.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md)|Obtiene la nueva propiedad.|  
  
## <a name="remarks"></a>Comentarios  
 Si una propiedad tiene un documento o secuencia de comandos asociados con él, la DE puede enviar este evento para el SDM para actualizar el **documentos de Script** ventana con el nombre del documento. El SDM llamará [GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md) con el argumento `guidDocument` para recuperar un `VARIANT` que contiene un [IUnknown](http://msdn.microsoft.com/library/e6b85472-e54b-4b8c-b19f-4454d6c05a8f) puntero. El SDM llamará [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) en este puntero para recuperar el [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interfaz que se usa para actualizar el **documentos de Script** ventana.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces del núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)

