---
title: IDebugObject2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugObject2
helpviewer_keywords:
- IDebugObject2 interface
ms.assetid: ef640967-8adb-4793-994d-ae1736510891
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8855d27448501abec506e3b363b41e64133c07fa
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63431663"
---
# <a name="idebugobject2"></a>IDebugObject2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> En Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información sobre la implementación de evaluadores de expresión de CLR, vea [evaluadores de expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [Managed expresión del evaluador de expresiones Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Esta interfaz proporciona información adicional sobre un objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugObject2 : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El evaluador de expresiones implementa esta interfaz para ofrecer compatibilidad con alias y el acceso a información sobre el objeto.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfaz puede obtener esta interfaz mediante [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3). Además, [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md) devuelve esta interfaz.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 Además de los métodos en el [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfaz, el `IDebugObject2` interfaz implementa lo siguiente:  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetBackingFieldForProperty](../../../extensibility/debugger/reference/idebugobject2-getbackingfieldforproperty.md)|Obtiene el campo o variable (si existe) que puede realizar copias de la propiedad representada por este objeto.|  
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugobject2-geticordebugvalue.md)|Obtiene el objeto de código administrado que representa el valor de este objeto.|  
|[CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)|Devuelve un alias existente o crea un identificador único para este objeto.|  
|[GetAlias](../../../extensibility/debugger/reference/idebugobject2-getalias.md)|Obtiene el alias asociado con este objeto, si existe.|  
|[GetField](../../../extensibility/debugger/reference/idebugobject2-getfield.md)|Obtiene el tipo de este objeto.|  
|[IsUserData](../../../extensibility/debugger/reference/idebugobject2-isuserdata.md)|Determina si este objeto representa datos de usuario.|  
|[IsEncOutdated](../../../extensibility/debugger/reference/idebugobject2-isencoutdated.md)|Determina si el estado de editar y continuar ya no es válido.<br /><br /> Un evaluador de expresiones personalizado no implementa este método (siempre debe devolver `E_NOTIMPL`).|  
  
## <a name="remarks"></a>Comentarios  
 Consulte [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) para obtener información sobre los alias.  
  
## <a name="requirements"></a>Requisitos  
 Header: ee.h  
  
 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de evaluación de expresión](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)   
 [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)
