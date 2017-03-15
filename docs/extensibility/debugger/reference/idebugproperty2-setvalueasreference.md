---
title: "IDebugProperty2::SetValueAsReference | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty2::SetValueAsReference"
helpviewer_keywords: 
  - "IDebugProperty2::SetValueAsReference (método)"
ms.assetid: 341b1b89-4ab8-4e1c-abe2-fb955df5c6b0
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugProperty2::SetValueAsReference
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Establece el valor de esta propiedad en el valor de referencia especificada.  
  
## Sintaxis  
  
```cpp#  
HRESULT SetValueAsReference(  
   IDebugReference2** rgpArgs,  
   DWORD              dwArgCount,  
   IDebugReference2*  pValue,  
   DWORD              dwTimeout  
);  
```  
  
```c#  
int SetValueAsReference(  
   IDebugReference2[] rgpArgs,  
   uint               dwArgCount,  
   IDebugReference2   pValue,  
   uint               dwTimeout  
);  
```  
  
#### Parámetros  
 `rgpArgs`  
 \[in\]  Una matriz de argumentos al establecedor de la propiedad de código administrado.  Si el establecedor de la propiedad no acepta argumentos o si este objeto de [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) no hace referencia a dicha establecedor de la propiedad, `rgpArgs` debe ser un valor NULL.  Este parámetro es normalmente un valor nulo.  
  
 `dwArgCount`  
 \[in\]  El número de argumentos en la matriz de `rgpArgs` .  
  
 `pValue`  
 \[in\]  Una referencia, en forma de objeto de [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) , el valor al uso de establecer esta propiedad.  
  
 `dwTimeout`  
 \[in\]  cuánto tiempo tomar para establecer el valor, en milisegundos.  un valor típico es `INFINITE`.  Esto afecta al tiempo que cualquier evaluación posible puede tomar.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; si no devuelve un código de error, normalmente uno de los siguientes:  
  
|Error|Descripción|  
|-----------|-----------------|  
|`E_SETVALUEASREFERENCE_NOTSUPPORTED`|establecer el valor de una referencia no se admite.|  
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|El valor no puede establecerse, como esta propiedad hace referencia a un método.|  
|`E_SETVALUE_VALUE_IS_READONLY`|El valor es de solo lectura y no se puede establecer.|  
|`E_NOTIMPL`|Este método no está implementado.|  
  
## Vea también  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)