---
title: "IDebugDocumentContext2::GetStatementRange | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentContext2::GetStatementRange"
helpviewer_keywords: 
  - "IDebugDocumentContext2::GetStatementRange"
ms.assetid: bc94851a-0ec4-47ea-99c7-0a585e54e726
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDocumentContext2::GetStatementRange
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtiene el intervalo de la instrucción del contexto del documento.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetStatementRange(   
   TEXT_POSITION* pBegPosition,  
   TEXT_POSITION* pEndPosition  
);  
```  
  
```c#  
int GetStatementRange(   
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
 Un intervalo de la instrucción es el intervalo de las líneas que contribuyeron código al que este contexto de documento consulta.  
  
 Para obtener el intervalo de código fuente \(comentarios incluida dentro de este contexto de documento, llame al método de [GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md) .  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo implementar este método para un objeto simple de `CDebugContext` que expone la interfaz de [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) .  Este ejemplo completa fin colocar sólo si la posición inicial no es un valor null.  
  
```cpp#  
HRESULT CDebugContext::GetStatementRange(TEXT_POSITION* pBegPosition,  
                                         TEXT_POSITION* pEndPosition)    
{    
   HRESULT hr;    
  
   // Check for a valid beginning position argument pointer.    
   if (pBegPosition)    
   {    
      // Copy the member TEXT_POSITION into the local pBegPosition.    
      memcpy(pBegPosition, &m_pos, sizeof (TEXT_POSITION));    
  
      // Check for a valid ending position argument pointer.   
     if (pEndPosition)    
      {    
         // Copy the member TEXT_POSITION into the local pEndPosition.    
         memcpy(pEndPosition, &m_pos, sizeof (TEXT_POSITION));    
      }    
      hr = S_OK;    
   }    
   else    
   {    
      hr = E_INVALIDARG;    
   }    
  
   return hr;    
}    
```  
  
## Vea también  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)   
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md)