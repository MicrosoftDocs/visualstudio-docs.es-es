---
title: IDebugPortEvents2 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugPortEvents2
helpviewer_keywords:
- IDebugPortEvents2 interface
ms.assetid: 2c017094-3ba2-4067-83f9-147df1d96bce
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3eb6208d815e4951bd916d014cddfdda34a8e589
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47576935"
---
# <a name="idebugportevents2"></a>IDebugPortEvents2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [IDebugPortEvents2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugportevents2).  
  
Esta interfaz notifica a un agente de escucha (normalmente, el Administrador de depuración de sesión [SDM] o un motor de depuración) de programa y el proceso de creación y destrucción en un puerto determinado. Esta información puede usarse para presentar una vista en tiempo real de los procesos y los programas que se ejecutan en el puerto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugPortEvents2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Visual Studio normalmente implementa esta interfaz para recibir notificaciones sobre la creación de programas y destrucción. Un motor de depuración también puede implementar esta interfaz para realizar escuchas de dichos eventos de puerto.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Todos los [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interfaces se pueden consultar para un <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interfaz. El <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.FindConnectionPoint%2A> método para `IDebugPortEvents2` se llama en el <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interfaz para obtener un <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interfaz. Por último, el <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> método en el <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interfaz se denomina para enviar eventos a través de la [eventos](../../../extensibility/debugger/reference/idebugportevents2-event.md) método.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 En la tabla siguiente se muestra el método de `IDebugPortEvents2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)|Envía eventos que describen la creación y destrucción de procesos y programas en el puerto.|  
  
## <a name="remarks"></a>Comentarios  
 `IDebugPortEvents2` También se usa por el SDM para depurar programas que se ejecutan en un proceso que ya se está depurando.  
  
 Eventos de puerto se pasan en el SDM por esta interfaz.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces del núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)

