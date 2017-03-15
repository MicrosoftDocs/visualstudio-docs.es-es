---
title: "IDebugDisassemblyStream2::GetCodeLocationId | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDisassemblyStream2::GetCodeLocationId"
helpviewer_keywords: 
  - "IDebugDisassemblyStream2::GetCodeLocationId"
ms.assetid: 567adfb8-2f54-499a-a027-e4ecb82277ef
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDisassemblyStream2::GetCodeLocationId
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Devuelve un identificador de la ubicación del código para un contexto de código determinado.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetCodeLocationId(   
   IDebugCodeContext2* pCodeContext,  
   UINT64*             puCodeLocationId  
);  
```  
  
```c#  
int GetCodeLocationId(   
   IDebugCodeContext2 pCodeContext,  
   out ulong          puCodeLocationId  
);  
```  
  
#### Parámetros  
 `pCodeContext`  
 \[in\]  Un objeto de [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) para convertirse en un identificador.  
  
 `puCodeLocationId`  
 \[out\]  Devuelve el identificador de la ubicación del código.  Vea la sección Comentarios.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  Devuelve `E_CODE_CONTEXT_OUT_OF_SCOPE` si el contexto del código es válido pero fuera del ámbito.  
  
## Comentarios  
 El identificador de la ubicación del código es específico del motor \(DE\) de depuración que admite desensamblado.  Este identificador de ubicación se utiliza internamente por el OF para seguir posiciones en el código y normalmente es una dirección o un desplazamiento de alguna clase.  El único requisito es que si el contexto del código de una ubicación es menor que el contexto del código de otra ubicación, el identificador correspondiente de la ubicación del código del primer contexto de código también debe ser menor que el identificador de la ubicación del código del segundo contexto de código.  
  
 Para recuperar el contexto del código de un identificador de la ubicación del código, llame al método de [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md) .  
  
## Vea también  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)