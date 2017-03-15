---
title: "IDebugSymbolProvider::GetAddressesFromContext | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugSymbolProvider::GetAddressesFromContext"
helpviewer_keywords: 
  - "IDebugSymbolProvider::GetAddressesFromContext (método)"
ms.assetid: a3124883-a255-4543-a5ec-e1c7a97beb69
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugSymbolProvider::GetAddressesFromContext
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Este método asigna un contexto del documento en una matriz de direcciones de depuración.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetAddressesFromContext(   
   IDebugDocumentContext2* pDocContext,  
   BOOL                    fStatmentOnly,  
   IEnumDebugAddresses**   ppEnumBegAddresses,  
   IEnumDebugAddresses**   ppEnumEndAddresses  
);  
```  
  
```c#  
int GetAddressesFromContext(  
   IDebugDocumentContext2  pDocContext,  
   bool                    fStatmentOnly,  
   out IEnumDebugAddresses ppEnumBegAddresses,  
   out IEnumDebugAddresses ppEnumEndAddresses  
);  
```  
  
#### Parámetros  
 `pDocContext`  
 \[in\]  El contexto del documento.  
  
 `fStatmentOnly`  
 \[in\]  Si es TRUE, límites que la depuración dirige a una sola instrucción.  
  
 `ppEnumBegAddresses`  
 \[out\]  Devuelve un enumerador para las direcciones de depuración que comienzan asociado a esta instrucción o línea.  
  
 `ppEnumEndAddresses`  
 \[out\]  Devuelve un enumerador de [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) para las direcciones de depuración de cierre asociado a esta instrucción o línea.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Un contexto de documento indica normalmente un intervalo de líneas de código fuente.  Este método proporciona instrucciones de depuración inicial y final asociado a estas líneas.  Algunos lenguajes permiten instrucciones que abarcan varias líneas, o las que contiene más de una instrucción.  Este método proporciona un marcador para limitar las direcciones de depuración a una sola instrucción.  
  
 Es posible que una sola instrucción tiene varias direcciones de depuración, como en el caso de las plantillas.  
  
## Vea también  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)   
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)