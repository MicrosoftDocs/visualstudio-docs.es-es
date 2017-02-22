---
title: "IDebugMethodField::GetThis | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMethodField::GetThis"
helpviewer_keywords: 
  - "IDebugMethodField::GetThis (método)"
ms.assetid: cc235bea-e909-4d8c-ab54-936736c803fc
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugMethodField::GetThis
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtiene el puntero de `this` \(`Me` en [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]\) del objeto que contiene el método.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetThis(   
   IDebugClassField** ppClass  
);  
```  
  
```c#  
int GetThis(  
   out IDebugClassField ppClass  
);  
```  
  
#### Parámetros  
 `ppClass`  
 \[out\]  Devuelve un objeto de [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) que representa el puntero “this”.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve S\_OK; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 En lenguajes orientados a objetos, normalmente hay puntero implícitamente al ámbito actual de una clase.  Esto se conoce como `this` en C\#\/C\+\+ como `Me` en [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)].  
  
## Vea también  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)