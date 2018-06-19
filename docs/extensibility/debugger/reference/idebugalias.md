---
title: IDebugAlias | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugAlias
helpviewer_keywords:
- IDebugAlias interface
ms.assetid: 3cc4c9a4-7805-4239-b00e-eb4a024f3c55
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f77e62b2dc36bb03b2145361cdea7dd9e65b2d32
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31102904"
---
# <a name="idebugalias"></a>IDebugAlias
> [!IMPORTANT]
>  Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información acerca de cómo implementar los evaluadores de expresión de CLR, vea [evaluadores de expresión de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [Managed expresión evaluador Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Representa un alias para una variable numérico. Un alias es simplemente un nombre diferente para una variable.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugAlias : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El evaluador de expresiones (EE) implementa esta interfaz para admitir alias numéricos para las variables.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md) crea un alias para un objeto determinado. Para buscar los alias, utilice [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md) o [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md).  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 Los métodos siguientes se definen en el `IDebugAlias` interfaz.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)|Obtiene el objeto al que hace referencia este alias.|  
|[GetName](../../../extensibility/debugger/reference/idebugalias-getname.md)|Obtiene el nombre de alias.|  
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugalias-geticordebugvalue.md)|Recupera un `ICorDebugValue` interfaz que proporciona acceso a administra información de código sobre este objeto (solo para código administrado).|  
|[Dispose](../../../extensibility/debugger/reference/idebugalias-dispose.md)|Marca este alias que ya no se está usando.|  
  
## <a name="remarks"></a>Comentarios  
 Un alias es un número decimal en forma de cadena seguido por el carácter #, por ejemplo, 1001#.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de evaluación de expresión](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)   
 [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)   
 [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)