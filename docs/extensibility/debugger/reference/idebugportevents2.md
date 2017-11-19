---
title: IDebugPortEvents2 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPortEvents2
helpviewer_keywords: IDebugPortEvents2 interface
ms.assetid: 2c017094-3ba2-4067-83f9-147df1d96bce
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 75e0b83b81c0d0d80b29c6b9ab32826402fcec99
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="idebugportevents2"></a>IDebugPortEvents2
Esta interfaz notifica a un agente de escucha (normalmente el Administrador de depuración de sesión [SDM] o un motor de depuración) de proceso y programa la creación y destrucción en un puerto concreto. Esta información puede utilizarse para presentar una vista en tiempo real de los procesos y los programas que se ejecutan en el puerto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugPortEvents2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Normalmente, Visual Studio implementa esta interfaz para recibir notificaciones sobre el programa creación y destrucción. Un motor de depuración también puede implementar esta interfaz para realizar escuchas de dichos eventos de puerto.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Todos los [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interfaces se pueden consultar para un <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interfaz. La <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.FindConnectionPoint%2A> método para `IDebugPortEvents2` se llama el <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interfaz para obtener un <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interfaz. Por último, el <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> método en el <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interfaz se llama para enviar los eventos a través de la [eventos](../../../extensibility/debugger/reference/idebugportevents2-event.md) método.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 En la tabla siguiente muestra el método de `IDebugPortEvents2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)|Envía eventos que describen la creación y destrucción de procesos y programas en el puerto.|  
  
## <a name="remarks"></a>Comentarios  
 `IDebugPortEvents2`También se utiliza por el SDM para depurar programas que se ejecutan en un proceso que ya se está depurando.  
  
 Eventos de puerto se pasan a la SDM por esta interfaz.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)