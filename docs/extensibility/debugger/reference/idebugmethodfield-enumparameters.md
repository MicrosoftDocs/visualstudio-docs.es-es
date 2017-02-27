---
title: "IDebugMethodField::EnumParameters | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMethodField::EnumParameters"
helpviewer_keywords: 
  - "IDebugMethodField::EnumParameters (método)"
ms.assetid: d77b1197-deb6-4144-8d1b-8b09949ccfac
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugMethodField::EnumParameters
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Crea un enumerador para los parámetros del método.  
  
## Sintaxis  
  
```cpp#  
HRESULT EnumParameters(   
   IEnumDebugFields** ppParams  
);  
```  
  
```c#  
int EnumParameters(  
   out IEnumDebugFields ppParams  
);  
```  
  
#### Parámetros  
 `ppParams`  
 \[out\]  Devuelve un objeto de [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) que representa la lista de parámetros al método; de lo contrario, devuelve un valor NULL si no hay parámetros.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve S\_OK o devuelve S\_FALSE si no hay parámetros.  De lo contrario, devuelve un código de error.  
  
## Comentarios  
 Cada elemento es un objeto de [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) que representa diferentes tipos de parámetros.  Llame al método de [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) en cada objeto para determinar exactamente qué clase de parámetro representa el objeto.  
  
 Un parámetro incluye el nombre de variable y su tipo.  El primer parámetro a un método de clase es normalmente el puntero “this”.  
  
 Si solo los tipos de los parámetros son necesarios, llame al método de [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) .  
  
## Vea también  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)