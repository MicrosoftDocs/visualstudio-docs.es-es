---
title: "IDebugDisassemblyStream2::GetCurrentLocation | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDisassemblyStream2::GetCurrentLocation"
helpviewer_keywords: 
  - "IDebugDisassemblyStream2::GetCurrentLocation"
ms.assetid: 512302f1-12b1-4107-8a6e-c5bc878ce1c3
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDisassemblyStream2::GetCurrentLocation
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Devuelve un identificador de la ubicación del código que representa la ubicación actual del código.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetCurrentLocation(   
   UINT64* puCodeLocationId  
);  
```  
  
```c#  
int GetCurrentLocation(   
   out ulong puCodeLocationId  
);  
```  
  
#### Parámetros  
 `puCodeLocationId`  
 \[out\]  Devuelve el identificador de la ubicación del código.  Vea la sección comentarios para el método de [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) para obtener una descripción de un identificador de la ubicación del código.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 El identificador de la ubicación del código se puede convertir en un contexto del código llamando al método de [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md) .  
  
## Vea también  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)