---
title: "IDebugSymbolProvider::GetNamespacesUsedAtAddress | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugSymbolProvider::GetNamespacesUsedAtAddress"
helpviewer_keywords: 
  - "IDebugSymbolProvider::GetNamespacesUsedAtAddress (método)"
ms.assetid: 392de54b-9af0-4567-953b-1b41acd1e05c
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugSymbolProvider::GetNamespacesUsedAtAddress
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Este método crea un enumerador para los espacios de nombres asociado con la dirección de la depuración.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetNamespacesUsedAtAddress(   
   IDebugAddress*     pAddress,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```c#  
int GetNamespacesUsedAtAddress(  
   IDebugAddress        pAddress,  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### Parámetros  
 `pAddress`  
 \[in\]  La dirección de depuración.  
  
 `ppEnum`  
 \[out\]  Devuelve un enumerador de [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) para los espacios de nombres.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Puede haber varios espacios de nombres asociado con una dirección especificada de depuración, por ejemplo, espacios de nombres anidados o varias instrucciones de `using` .  
  
## Vea también  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)