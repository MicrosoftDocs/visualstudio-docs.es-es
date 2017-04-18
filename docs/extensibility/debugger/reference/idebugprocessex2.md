---
title: IDebugProcessEx2 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProcessEx2
helpviewer_keywords:
- IDebugProcessEx2 interface
ms.assetid: 44e309ba-1d6f-499b-aa7e-9b34858a6d57
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 56483c55810f75042184439be9f0d7bcfb2d6836
ms.lasthandoff: 04/05/2017

---
# <a name="idebugprocessex2"></a>IDebugProcessEx2
Esta interfaz permite a la sesión de administrador de depuración (SDM) notificar a un proceso que se adjunte a o desasociar del proceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugProcessEx2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Un proveedor de puerto personalizado implementa esta interfaz en el mismo objeto que la [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) con el fin de la interfaz:  
  
-   Compatibilidad con seguimiento de las sesiones conectadas a un proceso  
  
-   Compatibilidad con la asociación automática a través de varios motores de depuración  
  
 El proveedor del puerto personalizado puede implementar esta interfaz si así lo decide.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
  
-   Las llamadas SDM [QueryInterface](/cpp/atl/queryinterface) en un `IDebugProcess2` interfaz para obtener esta interfaz.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDebugProcessEx2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[Asociar](../../../extensibility/debugger/reference/idebugprocessex2-attach.md)|Indica que el proceso que una sesión es ahora el proceso de depuración.|  
|[Desasociar](../../../extensibility/debugger/reference/idebugprocessex2-detach.md)|Indica que el proceso que una sesión ya no está depurando el proceso.|  
|[AddImplicitProgramNodes](../../../extensibility/debugger/reference/idebugprocessex2-addimplicitprogramnodes.md)|Agrega nodos de programa para obtener una lista de motores de depuración.|  
  
## <a name="remarks"></a>Comentarios  
 Esta interfaz es privada entre el SDM y el proceso.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Portpriv.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
