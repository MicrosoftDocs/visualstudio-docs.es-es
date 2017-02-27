---
title: "IDebugMethodField::EnumArguments | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMethodField::EnumArguments"
helpviewer_keywords: 
  - "IDebugMethodField::EnumArguments (método)"
ms.assetid: 3ab55488-2437-4ff6-a9ae-78ea6d7b23a8
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugMethodField::EnumArguments
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Crea un enumerador para el tipo de cada argumento necesario llamar al método.  
  
## Sintaxis  
  
```cpp#  
HRESULT EnumArguments(   
   IEnumDebugFields** ppParams  
);  
```  
  
```c#  
int EnumArguments(  
   out IEnumDebugFields ppParams  
);  
```  
  
#### Parámetros  
 `ppParams`  
 \[out\]  Devuelve un objeto de [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) que representa la lista de tipos de argumento.  Devuelve un valor NULL si no hay ningún argumento.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve S\_OK o devuelve S\_FALSE si no hay ningún argumento.  De lo contrario, devuelve un código de error.  
  
## Comentarios  
 cada elemento es un objeto de [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) que representa los tipos de cada parámetro.  Llame al método de [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) para recuperar información sobre el tipo de cada parámetro.  
  
 Si el nombre del parámetro es necesario junto con el tipo, llame al método de [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md) .  
  
## Vea también  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)