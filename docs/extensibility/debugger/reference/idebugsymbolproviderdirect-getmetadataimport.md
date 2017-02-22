---
title: "IDebugSymbolProviderDirect::GetMetaDataImport | Microsoft Docs"
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
  - "GetMetaDataImport"
  - "IDebugSymbolProviderDirect::GetMetaDataImport"
ms.assetid: b51a492c-af00-4b08-93fb-6c19ee4916aa
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugSymbolProviderDirect::GetMetaDataImport
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Recupera información de importación de metadatos.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetMetaDataImport (  
    GUID*      guid,  
    DWORD      appID,  
    IUnknown** ppImport  
);  
```  
  
```c#  
int GetMetaDataImport (  
    Guid       guid,  
    uint       appID,  
    out object ppImport  
);  
```  
  
#### Parámetros  
 `guid`  
 \[in\]  identificador único para el módulo.  
  
 `appID`  
 \[in\]  Identificador del dominio de aplicación.  
  
 `ppImport`  
 \[out\]  Devuelve un objeto que contiene información sobre la importación de metadatos.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)