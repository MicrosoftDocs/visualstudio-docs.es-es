---
title: "IDebugClassField::GetEnclosingClass | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugClassField::GetEnclosingClass"
helpviewer_keywords: 
  - "IDebugClassField::GetEnclosingClass (método)"
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugClassField::GetEnclosingClass
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtiene la clase envolvente esta clase.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetEnclosingClass(   
   IDebugClassField** ppClassField  
);  
```  
  
```c#  
int GetEnclosingClass(  
   out IDebugClassField ppClassField  
);  
```  
  
#### Parámetros  
 `ppClassField`  
 \[out\]  Devuelve un objeto de [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) que representa la clase envolvente.  Devuelve un valor NULL si no hay ninguna clase envolvente.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve S\_OK; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Si la clase representada por este objeto de [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) es una clase anidada, el parámetro de `ppClassField` devuelve un objeto de `IDebugClassField` que representa la clase envolvente.  Por ejemplo, dada esta definición de clase:  
  
```  
class RootClass {  
   class NestedClass { }  
};  
```  
  
 Llamando al método de `GetEnclosingClass` en el objeto de `IDebugClassField` que representa la clase de `NestedClass` devuelve un objeto de `IDebugClassField` que representa la clase `RootClass`.  
  
## Vea también  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)