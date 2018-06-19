---
title: IDebugObject2 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugObject2
helpviewer_keywords:
- IDebugObject2 interface
ms.assetid: ef640967-8adb-4793-994d-ae1736510891
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d5e60c9e084872b08ec8d38b784b47969af2d52e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31118926"
---
# <a name="idebugobject2"></a>IDebugObject2
> [!IMPORTANT]
>  Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información acerca de cómo implementar los evaluadores de expresión de CLR, vea [evaluadores de expresión de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [Managed expresión evaluador Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Esta interfaz proporciona información adicional sobre un objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugObject2 : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El evaluador de expresiones implementa esta interfaz para ofrecer compatibilidad con alias y obtener acceso a información sobre el objeto.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfaz puede obtener esta interfaz mediante [QueryInterface](/cpp/atl/queryinterface). Además, [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md) devuelve esta interfaz.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 Además de los métodos en el [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfaz, el `IDebugObject2` interfaz implementa lo siguiente:  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetBackingFieldForProperty](../../../extensibility/debugger/reference/idebugobject2-getbackingfieldforproperty.md)|Obtiene el campo o la variable (si existe) que puede realizar una copia la propiedad representada por este objeto.|  
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugobject2-geticordebugvalue.md)|Obtiene el objeto de código administrado que representa el valor de este objeto.|  
|[CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)|Devuelve un alias existente o crea un identificador único para este objeto.|  
|[GetAlias](../../../extensibility/debugger/reference/idebugobject2-getalias.md)|Obtiene el alias asociado a este objeto, si existe.|  
|[GetField](../../../extensibility/debugger/reference/idebugobject2-getfield.md)|Obtiene el tipo de este objeto.|  
|[IsUserData](../../../extensibility/debugger/reference/idebugobject2-isuserdata.md)|Determina si este objeto representa datos de usuario.|  
|[IsEncOutdated](../../../extensibility/debugger/reference/idebugobject2-isencoutdated.md)|Determina si el estado de editar y continuar ya no es válido.<br /><br /> Un evaluador de expresiones personalizado no implementa este método (siempre debe devolver `E_NOTIMPL`).|  
  
## <a name="remarks"></a>Comentarios  
 Vea [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) para obtener información sobre los alias.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de evaluación de expresión](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)   
 [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)