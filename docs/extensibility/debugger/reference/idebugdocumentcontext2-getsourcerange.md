---
title: "IDebugDocumentContext2::GetSourceRange | Microsoft Docs"
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
  - "IDebugDocumentContext2::GetSourceRange"
helpviewer_keywords: 
  - "IDebugDocumentContext2::GetSourceRange"
ms.assetid: 5903c75e-5390-4d13-9314-1ee276255313
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDocumentContext2::GetSourceRange
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtiene el intervalo de código fuente de este contexto de documento.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetSourceRange(   
   TEXT_POSITION* pBegPosition,  
   TEXT_POSITION* pEndPosition  
);  
```  
  
```c#  
int GetSourceRange(   
   TEXT_POSITION[] pBegPosition,  
   TEXT_POSITION[] pEndPosition  
);  
```  
  
#### Parámetros  
 `pBegPosition`  
 \[in, out\]  Una estructura de [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md) se completa con la posición inicial.  Establezca este argumento en un valor nulo si esta información no es necesaria.  
  
 `pEndPosition`  
 \[in, out\]  Una estructura de [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md) se completa con la posición final.  Establezca este argumento en un valor nulo si esta información no es necesaria.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Un intervalo de origen es el intervalo completo del código fuente, la instrucción actual de nuevo justo después de la instrucción anterior que contribuyó código.  El intervalo de origen se utiliza normalmente para mezclar las instrucciones de origen, como comentarios, con código en la ventana de desensamblado.  
  
 Para obtener el intervalo sólo para las instrucciones de código incluidas en este contexto de documento, llame al método de [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) .  
  
## Vea también  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)   
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md)