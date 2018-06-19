---
title: IDebugModule2 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugModule2
helpviewer_keywords:
- IDebugModule2 interface
ms.assetid: 24c2a126-f4ab-4891-8509-8ef99b994c08
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ac5c39ed386763689d504eda7a85e6a77fab4db3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31115598"
---
# <a name="idebugmodule2"></a>IDebugModule2
Esta interfaz representa un módulo, es decir, una unidad ejecutable de un programa, como un archivo DLL.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugModule2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El motor de depuración (Alemania) implementa esta interfaz para representar un módulo y para proporcionar acceso a información acerca de ese módulo.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Una llamada a [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md) devuelve esta interfaz. Los envíos DE la [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) de la interfaz para el Administrador de depuración de sesión (SDM) mediante el [eventos](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) método.  
  
 Esta interfaz también puede ser devueltos en una [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) estructura (que es devuelto por una llamada a [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)).  
  
 [Siguiente](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md) también devuelve esta interfaz ([EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) devuelve el [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md) interfaz).  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDebugModule2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)|Obtiene el [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) que describe este módulo.|  
|[ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)|OBSOLETO. NO UTILICE. Vuelve a cargar los símbolos para este módulo.|  
  
## <a name="remarks"></a>Comentarios  
 Información del módulo puede mostrarse en el **módulos** ventana del IDE.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)   
 [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)   
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)