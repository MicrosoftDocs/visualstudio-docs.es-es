---
title: "IDebugClassField::EnumConstructors | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugClassField::EnumConstructors"
helpviewer_keywords: 
  - "IDebugClassField::EnumConstructors (método)"
ms.assetid: 66a250b2-75a0-45aa-8d58-40f91cc4bf7b
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugClassField::EnumConstructors
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Crea un enumerador para los constructores para esta clase.  
  
## Sintaxis  
  
```cpp#  
HRESULT EnumConstructors(   
   CONSTRUCTOR_ENUM   cMatch,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```c#  
int EnumConstructors(  
   CONSTRUCTOR_ENUM     cMatch,   
   out IEnumDebugFields ppEnum  
);  
```  
  
#### Parámetros  
 `cMatch`  
 \[in\]  Un valor de enumeración de [CONSTRUCTOR\_ENUM](../../../extensibility/debugger/reference/constructor-enum.md) que especifica el tipo de constructores a la enumeración.  
  
 `ppEnum`  
 \[out\]  devuelve un objeto de [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) que representa la lista de constructores.  Devuelve un valor NULL si no hay constructores.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve S\_OK o devuelve S\_FALSE si no hay constructores.  De lo contrario, devuelve un código de error.  
  
## Comentarios  
 Cada elemento de la enumeración es un objeto de [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) que describe un método de constructor.  
  
 La lista de constructores no incluye normalmente los constructores predeterminados proporcionados por un compilador.  
  
## Vea también  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [CONSTRUCTOR\_ENUM](../../../extensibility/debugger/reference/constructor-enum.md)