---
title: IDebugReference2 | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugReference2
helpviewer_keywords:
- IDebugReference2 interface
ms.assetid: 3cfed312-f532-4bce-84a5-1677c14567d7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: df5eb1558cf2d93866eaa50e3a480ba70f904fe8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53855249"
---
# <a name="idebugreference2"></a>IDebugReference2
Esta interfaz representa una referencia a una propiedad de marco de pila o alguna otra propiedad.  
  
> [!NOTE]
>  `IDebugReference2` está reservado para uso futuro y todos sus métodos deben devolver `E_NOTIMPL`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugReference2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 La DE implementa esta interfaz para representar una referencia a un determinado tipo de valor. Por ejemplo, el valor podría ser un valor numérico como resultado de evaluación de una expresión, un contexto de la memoria utilizada para mostrar la memoria o una lista de registros y sus valores.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Llame a [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md) para obtener esta interfaz. [GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md) y [GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md) también devolver esta interfaz.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDebugReference2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)|Obtiene el [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) estructura que describe esta referencia.|  
|[SetValueAsString](../../../extensibility/debugger/reference/idebugreference2-setvalueasstring.md)|Establece el valor de esta referencia de una cadena.|  
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugreference2-setvalueasreference.md)|Establece el valor de esta referencia desde otra referencia.|  
|[EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)|Enumera a los elementos secundarios de esta referencia.|  
|[GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md)|Obtiene al elemento primario de esta referencia.|  
|[GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md)|Obtiene la referencia más derivado de esta referencia.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)|Obtiene los bytes de memoria al que hace referencia esta referencia.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)|Obtiene un contexto de la memoria para esta referencia.|  
|[GetSize](../../../extensibility/debugger/reference/idebugreference2-getsize.md)|Obtiene el tamaño, en bytes, de esta referencia.|  
|[SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)|Establece este tipo de referencia.|  
|[Compare](../../../extensibility/debugger/reference/idebugreference2-compare.md)|Compara esta referencia con otro.|  
  
## <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  Este uso de "propiedad" no debe confundirse con la que lo que significa que una variable de miembro de una clase, aunque un `IDebugReference2` puede representar dicha entidad.  
  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) representa una propiedad, mientras que `IDebugReference2` representa una referencia a una propiedad, normalmente una referencia a un objeto en el programa que se está depurando.  
  
 La diferencia principal entre una propiedad y una referencia es que una propiedad hace referencia a una instancia con nombre de un objeto, mientras que una referencia se refiere a una instancia sin nombre. Por ejemplo, una propiedad puede hacer referencia a un objeto en el montón del programa por `"a.b"`. Otra propiedad puede hacer referencia al mismo objeto como `"c.d"`. La manera de hacer referencia a esta propiedad requiere que `"a.b"` o `"c.d"` en el ámbito. Una referencia a este objeto mismo es anónimos; el objeto se puede hacer referencia a siempre y cuando la memoria para ese objeto es válida.  
  
 Un `IDebugProperty2` interfaz puede considerarse como un valor con un nombre, un tipo y una dirección. Un `IDebugReference2`, por otro lado, puede considerarse como un tipo y una dirección.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces del núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)