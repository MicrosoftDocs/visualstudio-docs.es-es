---
title: IDebugObject | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugObject
helpviewer_keywords:
- IDebugObject interface
ms.assetid: 05cd8bf4-c9ee-4b49-b782-2263c33067d6
caps.latest.revision: 14
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
ms.openlocfilehash: 4707784dcccfa85f0edee277bc40ed19013509b5
ms.lasthandoff: 04/05/2017

---
# <a name="idebugobject"></a>IDebugObject
> [!IMPORTANT]
>  Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información acerca de cómo implementar los evaluadores de expresión de CLR, vea [evaluadores de expresión de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [Managed expresión evaluador Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Esta interfaz representa un objeto que crea el enlazador para encapsular los valores de símbolos y expresiones.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugObject : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Un evaluador de expresiones implementa esta interfaz para representar un objeto.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Esta interfaz es la clase base para todos los objetos que el evaluador de expresiones se usa en expresiones analizadas. Se devuelve mediante una llamada a la [enlazar](../../../extensibility/debugger/reference/idebugbinder-bind.md) método. [QueryInterface](/cpp/atl/queryinterface) Obtiene las interfaces más especializadas de esta interfaz.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDebugObject`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md)|Obtiene el tamaño del objeto.|  
|[GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)|Obtiene el valor del objeto como una serie de bytes consecutiva.|  
|[SetValue](../../../extensibility/debugger/reference/idebugobject-setvalue.md)|Establece el valor del objeto de una serie de bytes consecutiva.|  
|[SetReferenceValue](../../../extensibility/debugger/reference/idebugobject-setreferencevalue.md)|Establece el valor de referencia de este objeto.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugobject-getmemorycontext.md)|Obtiene el contexto de memoria que representa la dirección del valor del objeto.|  
|[GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md)|Crea una copia del objeto administrado en el espacio de direcciones del motor de depuración.|  
|[IsNullReference](../../../extensibility/debugger/reference/idebugobject-isnullreference.md)|Comprueba si este objeto es una referencia nula.|  
|[IsEqual](../../../extensibility/debugger/reference/idebugobject-isequal.md)|Compara un objeto a este.|  
|[IsReadOnly](../../../extensibility/debugger/reference/idebugobject-isreadonly.md)|Determina si este objeto es de solo lectura.|  
|[IsProxy](../../../extensibility/debugger/reference/idebugobject-isproxy.md)|Determina si el objeto es un proxy transparente.|  
  
## <a name="remarks"></a>Comentarios  
 El evaluador de expresiones utiliza esta interfaz como clase base para representar objetos en un árbol de análisis.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de evaluación de expresión](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)   
 [Enlazar](../../../extensibility/debugger/reference/idebugbinder-bind.md)
