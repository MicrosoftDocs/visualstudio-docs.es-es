---
title: "IDebugSymbolProviderDirect::GetAppIDFromAddress | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugSymbolProviderDirect::GetAppIDFromAddress"
  - "GetAppIDFromAddress"
ms.assetid: d76a0f36-79c4-4c58-9db3-880b00d11610
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSymbolProviderDirect::GetAppIDFromAddress
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Recupera el identificador del dominio de aplicación determinado la dirección de depuración.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetAppIDFromAddress(  
   IDebugAddress* pAddress,  
   DWORD*         pAppID  
);  
```  
  
```c#  
int GetAppIDFromAddress(  
   IDebugAddress pAddress,  
   out uint      pAppID  
);  
```  
  
#### Parámetros  
 `pAddress`  
 \[in\]  Depurar la dirección representada por la interfaz de [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .  
  
 `pAppID`  
 \[out\]  Identificador del dominio de aplicación.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)