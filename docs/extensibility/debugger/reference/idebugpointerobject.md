---
title: IDebugPointerObject | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPointerObject
helpviewer_keywords:
- IDebugPointerObject interface
ms.assetid: 257fa167-b46e-4ffb-9a12-272efbf26702
caps.latest.revision: 11
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
ms.openlocfilehash: 0fbc9ae8e067a3442135e436712c1dc47360e339
ms.lasthandoff: 04/05/2017

---
# <a name="idebugpointerobject"></a>IDebugPointerObject
> [!IMPORTANT]
>  Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información acerca de cómo implementar los evaluadores de expresión de CLR, vea [evaluadores de expresión de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [Managed expresión evaluador Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Esta interfaz representa un objeto de puntero.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugPointerObject : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El evaluador de expresiones implementa esta interfaz para representar un objeto de puntero.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 El [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfaz puede obtener esta interfaz mediante [QueryInterface](/cpp/atl/queryinterface) si el `IDebugObject` representa un puntero.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 Además de los métodos heredados de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md), el `IDebugPointerObject` interfaz expone los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[Desreferencia](../../../extensibility/debugger/reference/idebugpointerobject-dereference.md)|Obtiene el objeto al que señala la interfaz.|  
|[GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)|Obtiene el valor al que hace referencia la interfaz como una serie de bytes consecutivos.|  
|[SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)|Establece el valor al que apunta la interfaz de una serie de bytes consecutivos.|  
  
## <a name="remarks"></a>Comentarios  
 Un evaluador de expresiones utiliza esta interfaz para representar un puntero en un árbol de análisis.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de evaluación de expresión](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
