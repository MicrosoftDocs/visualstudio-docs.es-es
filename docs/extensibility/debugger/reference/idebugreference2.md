---
title: "IDebugReference2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugReference2"
helpviewer_keywords: 
  - "Interfaz IDebugReference2"
ms.assetid: 3cfed312-f532-4bce-84a5-1677c14567d7
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugReference2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz representa una referencia a una propiedad del marco de pila o a alguna otra propiedad.  
  
> [!NOTE]
>  `IDebugReference2` se reserva para uso futuro, y todos sus métodos deben devolver `E_NOTIMPL`.  
  
## Sintaxis  
  
```  
IDebugReference2 : IUnknown  
```  
  
## Notas para los implementadores  
 El OF implementa esta interfaz para representar una referencia a una clase determinada de valor.  Por ejemplo, el valor puede ser un valor numérico como resultado de una evaluación de la expresión, un contexto de memoria utilizado para mostrar la memoria, o una lista de registros y sus valores.  
  
## Notas para los llamadores  
 llamada [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md) para obtener esta interfaz.  [GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md) y [GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md) también devuelven esta interfaz.  
  
## métodos en el orden de Vtable  
 La tabla siguiente se muestran los métodos de `IDebugReference2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)|Obtiene la estructura de [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) que describe la referencia.|  
|[SetValueAsString](../../../extensibility/debugger/reference/idebugreference2-setvalueasstring.md)|establece el valor de esta referencia de una cadena.|  
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugreference2-setvalueasreference.md)|establece el valor de esta referencia de otra referencia.|  
|[EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)|Enumera los elementos secundarios de esta referencia.|  
|[GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md)|obtiene el elemento primario de esta referencia.|  
|[GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md)|Obtiene la referencia más derivada de esta referencia.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)|Obtiene los bytes de memoria a las que esta referencia consulta.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)|Obtiene un contexto de memoria de esta referencia.|  
|[GetSize](../../../extensibility/debugger/reference/idebugreference2-getsize.md)|Obtiene el tamaño, en bytes, de esta referencia.|  
|[SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)|establece este tipo de referencia.|  
|[Comparar](../../../extensibility/debugger/reference/idebugreference2-compare.md)|compara esta referencia con otra.|  
  
## Comentarios  
  
> [!NOTE]
>  Este uso de “propiedad” no se debe confundir con ese significado una variable miembro de una clase, aunque `IDebugReference2` puede representar tal entidad.  
  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) representa una propiedad, mientras que `IDebugReference2` representa una referencia a una propiedad, normalmente una referencia a un objeto en el programa que se depura.  
  
 La diferencia principal entre una propiedad y una referencia es que una propiedad hace referencia a una instancia con nombre de un objeto, como una referencia a una instancia sin nombre.  Por ejemplo, una propiedad puede hacer referencia a un objeto en la pila de programa por `"a.b"`.  Otra propiedad puede hacer referencia al mismo objeto que `"c.d"`.  La manera de hacer referencia a esta propiedad requiere ese `"a.b"` o `"c.d"` está en el ámbito.  una referencia a este mismo objeto es anónima; el objeto puede hacer referencia a memoria para ese objeto es válida.  
  
 Una interfaz de `IDebugProperty2` se puede considerar como un valor con un nombre, tipo, y una dirección.  `IDebugReference2`, por otro lado, puede considerarse como un tipo y una dirección.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)