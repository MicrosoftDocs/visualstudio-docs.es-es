---
title: "IDebugClassField::EnumNestedClasses | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugClassField::EnumNestedClasses"
helpviewer_keywords: 
  - "IDebugClassField::EnumNestedClasses (método)"
ms.assetid: 2ba5ef0c-395e-4006-9e3c-9b06e1d711d0
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugClassField::EnumNestedClasses
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Crea un enumerador para las clases anidadas en esta clase.  
  
## Sintaxis  
  
```cpp#  
HRESULT EnumNestedClasses(   
   IEnumDebugFields** ppEnum  
);  
```  
  
```c#  
int EnumNestedClasses(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### Parámetros  
 `ppEnum`  
 \[out\]  devuelve un objeto de [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) que representa la lista de clases anidadas.  Devuelve un valor NULL si no hay clases anidadas.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve S\_OK o devuelve S\_FALSE si no hay clases anidadas.  De lo contrario, devuelve un código de error.  
  
## Comentarios  
 cada elemento de la enumeración es un objeto de [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) que describe una clase anidada.  
  
 Una clase es una clase definida en otra clase.  Por ejemplo:  
  
```  
class RootClass {  
   class NestedClass { }  
};  
```  
  
 La enumeración de [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) contendrá un objeto que representa la clase de `NestedClass` .  
  
## Vea también  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)