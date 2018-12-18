---
title: IDebugModule3 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugModule3
helpviewer_keywords:
- IDebugModule3 interface
ms.assetid: 44f8e96e-9c59-4ffc-9a08-9c908a0e4de7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0b74063aa73db8258b2986ac1310d02e36027bf6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31118458"
---
# <a name="idebugmodule3"></a>IDebugModule3
Esta interfaz representa un módulo que admite las ubicaciones alternativas de símbolos y Estados de JustMyCode.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugModule3 : IDebugModule2  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El motor de depuración (Alemania) implementa esta interfaz para admitir las ubicaciones alternativas de símbolos y para trabajar con los Estados de JustMyCode (vea la [Glosario de depurador de Visual Studio](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md) para una definición de "JustMyCode").  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Una llamada a [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md) devuelve esta interfaz. Los envíos DE la [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) de la interfaz para el Administrador de depuración de sesión (SDM) mediante el [eventos](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) método. Además, una llamada a [QueryInterface](/cpp/atl/queryinterface) en un [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) interfaz devuelve esta interfaz.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 Además de los métodos en el [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) interfaz, esta interfaz implementa los métodos siguientes:  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)|Devuelve una lista de rutas de acceso que se buscan los símbolos y los resultados de búsqueda de cada ruta de acceso.|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)|Carga e inicializa los símbolos del módulo actual.|  
|[IsUserCode](../../../extensibility/debugger/reference/idebugmodule3-isusercode.md)|Devuelve marca especifica si el módulo representa el código de usuario.|  
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugmodule3-setjustmycodestate.md)|Especifica si el módulo se debe considerar el código de usuario o no.|  
  
## <a name="remarks"></a>Comentarios  
 Visual Studio es el consumidor típico de esta interfaz.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)   
 [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)