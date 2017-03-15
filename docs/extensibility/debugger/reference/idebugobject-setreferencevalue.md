---
title: "IDebugObject::SetReferenceValue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugObject::SetReferenceValue"
helpviewer_keywords: 
  - "IDebugObject::SetReferenceValue (método)"
ms.assetid: 08c78a4e-98eb-41cb-8b75-02a6a43d49f7
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugObject::SetReferenceValue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

establece el valor de referencia de este objeto.  
  
## Sintaxis  
  
```cpp#  
HRESULT SetReferenceValue(   
   IDebugObject* pObject  
);  
```  
  
```c#  
int SetReferenceValue(  
   [In] IDebugObject pObject  
);  
```  
  
#### Parámetros  
 `pObject`  
 \[in\]  un objeto de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que representa el nuevo valor de referencia.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve S\_OK; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Este método crea este objeto de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) una referencia al valor del objeto especificado en el parámetro de `pObject` , producir aún cualquier referencia anterior.  Observe que este objeto de `IDebugObject` ya debe ser un tipo de referencia.  
  
## Vea también  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)