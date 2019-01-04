---
title: IDebugProgramNodeAttach2 | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgramNodeAttach2
helpviewer_keywords:
- IDebugProgramNodeAttach2 interface
ms.assetid: 46b37ac9-a026-4ad3-997b-f19e2f8deb73
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e212c195754fcab8d60beb3a6536606d6ce86054
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53851802"
---
# <a name="idebugprogramnodeattach2"></a>IDebugProgramNodeAttach2
Permite que un nodo de programa recibir una notificación de un intento para adjuntar al programa.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugProgramNodeAttach2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Esta interfaz se implementa en la misma clase que implementa el [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) interfaz con el fin de recibir una notificación de una operación de asociación y para proporcionar una oportunidad de cancelar la operación de adjuntar.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Esta interfaz se obtiene mediante una llamada a la `QueryInterface` método en un [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) objeto. El [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) método debe llamarse antes el [adjuntar](../../../extensibility/debugger/reference/idebugengine2-attach.md) método para dar el nodo programa una oportunidad para detener el proceso de adjuntar.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 Esta interfaz implementa el método siguiente:  
  
|Método|Descripción|  
|------------|-----------------|  
|[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)|Adjunta el programa asociado o se aplaza el proceso de conexión para el [adjuntar](../../../extensibility/debugger/reference/idebugengine2-attach.md) método.|  
  
## <a name="remarks"></a>Comentarios  
 Esta interfaz es la alternativa preferida para el desuso [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md) método. Todos los motores de depuración siempre se cargan con la `CoCreateInstance` de función, es decir, se crea una instancia fuera del espacio de direcciones del programa que se está depurando.  
  
 Si una implementación anterior de la `IDebugProgramNode2::Attach_V7` método simplemente se establecen el `GUID` del programa que se está depurando, a continuación, solo el [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) método debe implementarse.  
  
 Si una implementación anterior de la `IDebugProgramNode2::Attach_V7` método usa la interfaz de devolución de llamada que se ha proporcionado, a continuación, esa funcionalidad es necesario mover a una implementación de la [adjuntar](../../../extensibility/debugger/reference/idebugengine2-attach.md) método y el `IDebugProgramNodeAttach2` interfaz no se deben implementar.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Msdbg.h  
  
 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces del núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [Adjuntar](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)