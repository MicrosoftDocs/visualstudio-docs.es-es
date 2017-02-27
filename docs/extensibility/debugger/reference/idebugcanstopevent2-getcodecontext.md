---
title: "IDebugCanStopEvent2::GetCodeContext | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCanStopEvent2::GetCodeContext"
helpviewer_keywords: 
  - "IDebugCanStopEvent2::GetCodeContext"
ms.assetid: eecf08b6-f9b7-4358-941b-3a448a92ac62
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugCanStopEvent2::GetCodeContext
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtiene el contexto del código que describe la ubicación de este evento.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetCodeContext(   
   IDebugCodeContext2** ppCodeContext  
);  
```  
  
```c#  
int GetCodeContext(   
   out IDebugCodeContext2 ppCodeContext  
);  
```  
  
#### Parámetros  
 `ppCodeContext`  
 \[out\]  Devuelve el objeto de [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) que representa la ubicación actual del código.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Para la mayoría de las arquitecturas en tiempo de ejecución, un contexto del código se puede considerar como dirección en una secuencia de la ejecución del programa, apunte a una instrucción específica.  
  
 Para obtener el contexto del documento, que se orienta hacia las líneas de código fuente, llame al método de [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md) .  
  
## Vea también  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)