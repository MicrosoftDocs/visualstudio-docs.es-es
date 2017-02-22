---
title: "IDebugSymbolProvider::GetMethodFieldsByName | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugSymbolProvider::GetMethodFieldsByName"
helpviewer_keywords: 
  - "IDebugSymbolProvider::GetMethodFieldsByName (método)"
ms.assetid: 1f781320-81ef-4037-b068-f1864b271258
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugSymbolProvider::GetMethodFieldsByName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Este método obtiene el campo que representa un nombre completo del método.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetMethodFieldsByName(   
   LPCOLESTR          pszFullName,  
   NAME_MATCH         nameMatch,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```c#  
int GetMethodFieldsByName(  
   string               pszFullName,   
   NAME_MATCH           nameMatch,   
   out IEnumDebugFields ppEnum  
);  
```  
  
#### Parámetros  
 `pszFullName`  
 \[in\]  El nombre del método.  
  
 `nameMatch`  
 \[in\]  Selecciona el tipo de coincidencia, por ejemplo, distingue entre mayúsculas y minúsculas.  
  
 `ppEnum`  
 \[out\]  Devuelve un enumerador de [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) para los campos asociado a este método.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Un método puede asociar varios campos si se sobrecarga, por ejemplo.  
  
## Vea también  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)