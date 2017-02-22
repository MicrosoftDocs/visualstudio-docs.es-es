---
title: "IDebugSymbolProviderDirect::GetMethodFromAddress | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugSymbolProviderDirect::GetMethodFromAddress"
  - "GetMethodFromAddress"
ms.assetid: 33ffd197-1221-41bc-a9f6-f133ebdcb783
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugSymbolProviderDirect::GetMethodFromAddress
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Información de recupera sobre el método en la dirección especificada de depuración.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetMethodFromAddress(  
   IDebugAddress* pAddress,  
   GUID*          pGuid,  
   DWORD*         pAppID,  
   _mdToken*      pTokenClass,  
   _mdToken*      pTokenMethod,  
   DWORD*         pdwOffset,  
   DWORD*         pdwVersion  
);  
```  
  
```c#  
int GetMethodFromAddress(  
   IDebugAddress pAddress,  
   out Guid      pGuid,  
   out uint      pAppID,  
   out uint      pTokenClass,  
   out uint      pTokenMethod,  
   out uint      pdwOffset,  
   out uint      pdwVersion  
);  
```  
  
#### Parámetros  
 `pAddress`  
 \[in\]  Depurar la dirección representada por la interfaz de [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .  
  
 `pGuid`  
 \[out\]  Identificador único del módulo.  
  
 `pAppID`  
 \[out\]  Identificador del dominio de aplicación.  
  
 `pTokenClass`  
 \[out\]  Token que representa la clase contenedora.  
  
 `pTokenMethod`  
 \[out\]  símbolo que representa el módulo.  
  
 `pdwOffset`  
 \[out\]  Un desplazamiento de bytes desde el principio del parámetro de `pAddress` .  
  
 `pdwVersion`  
 \[out\]  Número de versión del método.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)