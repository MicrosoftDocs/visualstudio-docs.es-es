---
title: "IDebugProperty2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty2"
helpviewer_keywords: 
  - "Interfaz IDebugProperty2"
ms.assetid: a7d5c70f-a1a5-4120-9f70-184e01c25bff
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProperty2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz representa una propiedad del marco de pila, una propiedad de documento del programa, o alguna otra propiedad.  La propiedad suele ser el resultado de una evaluación de la expresión.  
  
> [!NOTE]
>  Este uso de “propiedad” no se debe confundir con ese significado una variable miembro de una clase, aunque `IDebugProperty2` puede representar tal entidad.  
  
## Sintaxis  
  
```  
IDebugProperty2 : IUnknown  
```  
  
## Notas para los implementadores  
 El OF implementa esta interfaz para representar un tipo determinado de valor.  Por ejemplo, el valor puede ser un valor numérico como resultado de una evaluación de la expresión, un contexto de memoria utilizado para mostrar la memoria, o una lista de registros y sus valores.  
  
## Notas para los llamadores  
 Llame a [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) o [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) para obtener esta interfaz, que representa el resultado de una evaluación.  `IDebugExpression2::EvaluateAsync` devuelve esta interfaz enviando una interfaz de [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) al SDM, que a su vez llama a [GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) para recuperar la propiedad.  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md) devuelve esta interfaz para proporcionar el documento asociado del script.  
  
 [GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md) devuelve esta interfaz para representar el valor devuelto de una función.  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md) devuelve esta interfaz para representar las diversas propiedades de programa como un nombre o un contexto de memoria.  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) devuelve esta interfaz para representar las diversas propiedades de marco de pila como variables locales.  
  
## métodos en el orden de Vtable  
 La tabla siguiente se muestran los métodos de `IDebugProperty2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)|Completa una estructura de [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) que describe una propiedad.|  
|[SetValueAsString](../../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md)|establece el valor de una propiedad de una cadena.|  
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugproperty2-setvalueasreference.md)|Establece el valor de la propiedad de una referencia determinada.|  
|[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)|Enumera los elementos secundarios de una propiedad.|  
|[GetParent](../../../extensibility/debugger/reference/idebugproperty2-getparent.md)|devuelve el elemento primario de una propiedad.|  
|[GetDerivedMostProperty](../../../extensibility/debugger/reference/idebugproperty2-getderivedmostproperty.md)|Devuelve la propiedad que describe la propiedad más derivada de una propiedad.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)|Devuelve los bytes de memoria que constituyen el valor de una propiedad.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)|Devuelve el contexto de memoria para un valor de propiedad.|  
|[GetSize](../../../extensibility/debugger/reference/idebugproperty2-getsize.md)|Devuelve el tamaño, en bytes, del valor de propiedad.|  
|[GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)|Devuelve una referencia al valor de propiedad.|  
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md)|Devuelve información extendida de una propiedad.|  
  
## Comentarios  
 Una propiedad, como se representa por una interfaz de `IDebugProperty2` , se puede considerar como un valor con un nombre, tipo, y una dirección.  en términos más generales, `IDebugProperty2` puede representar cualquier cosa que tiene una estructura jerárquica, con los elementos primarios y los nodos secundarios.  
  
 Una propiedad suele ser transitorio, durando sólo mientras el marco de pila actual, por ejemplo.  Por otra parte, una referencia, como se representa por una interfaz de [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) , dura mientras mantiene el valor en memoria.  
  
 El IDE puede utilizar la interfaz de `IDebugProperty2` para permitir a los usuarios examinar y modificar las propiedades en tiempo de ejecución.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)