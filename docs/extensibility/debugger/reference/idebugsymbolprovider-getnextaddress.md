---
title: "IDebugSymbolProvider::GetNextAddress | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugSymbolProvider::GetNextAddress"
helpviewer_keywords: 
  - "IDebugSymbolProvider::GetNextAddress (método)"
ms.assetid: 704eeb94-cb13-49d1-82b6-7d83ed0f19c0
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSymbolProvider::GetNextAddress
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtiene la dirección de depuración que sigue a una dirección determinada de depuración en un método.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetNextAddress(   
   IDebugAddress*  pAddress,  
   BOOL            fStatementOnly,  
   IDebugAddress** ppAddress  
);  
```  
  
```c#  
int GetNextAddress(   
   IDebugAddress     pAddress,  
   bool              fStatementOnly,  
   out IDebugAddress ppAddress  
);  
```  
  
#### Parámetros  
 `pAddress`  
 \[in\]  Dirección determinada de depuración.  
  
 `fStatementOnly`  
 \[in\]  Si es TRUE, límites que la depuración dirige a una sola instrucción.  
  
 `ppAddress`  
 \[out\]  Devuelve la dirección siguiente de depuración.  
  
## Valor devuelto  
 Devuelve `HRESULT`válido, normalmente S\_OK.  
  
## Vea también  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)