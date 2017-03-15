---
title: "IDebugSymbolProvider::GetAddressesFromPosition | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugSymbolProvider::GetAddressesFromPosition"
helpviewer_keywords: 
  - "IDebugSymbolProvider::GetAddressesFromPosition (método)"
ms.assetid: 1b0f02cb-8ace-4614-88f3-0e10239012b3
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugSymbolProvider::GetAddressesFromPosition
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Este método asigna una posición de documento en una matriz de direcciones de depuración.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetAddressesFromPosition(   
   IDebugDocumentPosition2* pDocPos,  
   BOOL                     fStatmentOnly,  
   IEnumDebugAddresses**    ppEnumBegAddresses,  
   IEnumDebugAddresses**    ppEnumEndAddresses  
);  
```  
  
```c#  
int GetAddressesFromPosition(   
   IDebugDocumentPosition2  pDocPos,  
   bool                     fStatmentOnly,  
   out IEnumDebugAddresses  ppEnumBegAddresses,  
   out IEnumDebugAddresses  ppEnumEndAddresses  
);  
```  
  
#### Parámetros  
 `pDocPos`  
 \[in\]  La posición del documento.  
  
 `fStatmentOnly`  
 \[in\]  Si es TRUE, límites que la depuración dirige a una sola instrucción.  
  
 `ppEnumBegAddresses`  
 \[out\]  Devuelve un enumerador para las direcciones de depuración que comienzan asociado a esta instrucción o línea.  
  
 `ppEnumEndAddresses`  
 \[out\]  Devuelve un enumerador de [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) para las direcciones de depuración de cierre asociado a esta instrucción o línea.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Un documento colocar normalmente indica un intervalo de líneas de código fuente.  Este método proporciona instrucciones de depuración inicial y final asociado a estas líneas.  Algunos lenguajes permiten instrucciones que abarcan varias líneas, o las que contiene más de una instrucción.  Este método proporciona un marcador para limitar las direcciones de depuración a una sola instrucción.  
  
 Es posible que una sola instrucción tiene varias direcciones de depuración, como en el caso de las plantillas.  
  
## Vea también  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)   
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)