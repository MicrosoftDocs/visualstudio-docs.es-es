---
title: IDebugAlias | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugAlias
helpviewer_keywords:
- IDebugAlias interface
ms.assetid: 3cc4c9a4-7805-4239-b00e-eb4a024f3c55
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a499cb2d5de9f0507039ec04d31b00d7aaec9ac9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51722025"
---
# <a name="idebugalias"></a>IDebugAlias
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  En Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información sobre la implementación de evaluadores de expresión de CLR, vea [evaluadores de expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [Managed expresión del evaluador de expresiones Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Representa un alias para una variable numérico. Un alias es simplemente un nombre diferente para una variable.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugAlias : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El evaluador de expresiones (EE) implementa esta interfaz para admitir los alias numéricos para las variables.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md) crea un alias para un objeto determinado. Para buscar los alias, use [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md) o [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md).  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 Los métodos siguientes se definen en el `IDebugAlias` interfaz.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)|Obtiene el objeto al que hace referencia este alias.|  
|[GetName](../../../extensibility/debugger/reference/idebugalias-getname.md)|Obtiene el nombre de alias.|  
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugalias-geticordebugvalue.md)|Recupera un `ICorDebugValue` administrados de interfaz que proporciona acceso a información de código sobre este objeto (solo código administrado).|  
|[Dispose](../../../extensibility/debugger/reference/idebugalias-dispose.md)|Marca este alias como ya no se usan.|  
  
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

