---
title: IDebugProgramEngines2 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramEngines2
helpviewer_keywords:
- IDebugProgramEngines2 interface
ms.assetid: 53d648f0-6c11-4337-badd-c43f3872b62c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 391e2852d83ff7a615438ce68b1aaaefb04d8654
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogramengines2"></a>IDebugProgramEngines2
Nodos de programa usa esta interfaz para especificar todos los posibles motores de depuración (Alemania) que pueden depurar este programa.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugProgramEngines2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Una DE o un proveedor de puerto personalizado implementa esta interfaz en el mismo objeto que implementa [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) que admite el establecimiento de un Alemania específico que se usará para un programa determinado.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Llame a [QueryInterface](/cpp/atl/queryinterface) en un `IDebugProgramNode2` interfaz para obtener esta interfaz.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDebugProgramEngines2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[EnumPossibleEngines](../../../extensibility/debugger/reference/idebugprogramengines2-enumpossibleengines.md)|Indica el posible DEs que puede depurar este programa.|  
|[SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md)|Selecciona la DE utilizar para depurar este programa.|  
  
## <a name="remarks"></a>Comentarios  
 Una vez que se elige un Alemania por el usuario, esa opción se registra con el nodo del programa mediante una llamada a [SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md). El motor seleccionado se convierte en el motor devuelto por [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md).  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)