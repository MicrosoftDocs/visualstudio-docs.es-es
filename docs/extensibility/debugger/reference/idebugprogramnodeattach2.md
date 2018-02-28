---
title: IDebugProgramNodeAttach2 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgramNodeAttach2
helpviewer_keywords:
- IDebugProgramNodeAttach2 interface
ms.assetid: 46b37ac9-a026-4ad3-997b-f19e2f8deb73
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 1ff6b3aa49030ed49a05cb81e0a949c7bc55806c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogramnodeattach2"></a>IDebugProgramNodeAttach2
Permite a un nodo de programa recibir una notificación de un intento para adjuntar al programa.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugProgramNodeAttach2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Esta interfaz se implementa en la misma clase que implementa el [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) interfaz con el fin de recibir una notificación de una operación de adjuntar y para proporcionar una oportunidad para cancelar la operación de adjuntar.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Obtener esta interfaz mediante una llamada a la `QueryInterface` método en un [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) objeto. El [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) método debe llamarse antes de la [adjuntar](../../../extensibility/debugger/reference/idebugengine2-attach.md) método para dar el nodo programa una oportunidad para detener el proceso de conexión.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 Esta interfaz implementa el método siguiente:  
  
|Método|Descripción|  
|------------|-----------------|  
|[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)|Se une al programa o pasa el proceso de conexión para el [adjuntar](../../../extensibility/debugger/reference/idebugengine2-attach.md) método.|  
  
## <a name="remarks"></a>Comentarios  
 Esta interfaz es la alternativa preferida para las regiones [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md) método. Siempre se cargan todos los motores de depuración con el `CoCreateInstance` de función, es decir, se crean instancias fuera del espacio de direcciones del programa que se está depurando.  
  
 Si una implementación anterior de la `IDebugProgramNode2::Attach_V7` método simplemente se establecer el `GUID` del programa que se está depurando, a continuación, solo el [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) método debe implementarse.  
  
 Si una implementación anterior de la `IDebugProgramNode2::Attach_V7` método usa la interfaz de devolución de llamada que se proporcionó, a continuación, esa funcionalidad debe moverse a una implementación de la [adjuntar](../../../extensibility/debugger/reference/idebugengine2-attach.md) método y `IDebugProgramNodeAttach2` interfaz no tiene que implementarse.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [Adjuntar](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)