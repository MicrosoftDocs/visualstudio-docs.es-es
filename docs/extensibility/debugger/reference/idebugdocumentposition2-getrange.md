---
title: "IDebugDocumentPosition2::GetRange | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentPosition2::GetRange"
helpviewer_keywords: 
  - "IDebugDocumentPosition2::GetRange"
ms.assetid: 91a06ee7-253a-4215-be22-04bf57305aa8
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDocumentPosition2::GetRange
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtiene el intervalo para esta posición del documento.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetRange(   
   TEXT_POSITION* pBegPosition,  
   TEXT_POSITION* pEndPosition  
);  
```  
  
```c#  
int GetRange(   
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
 El intervalo especificado en una posición del documento para un punto de interrupción de ubicación es utilizado por el motor de depuración \(DE\) para buscar a continuación para una instrucción que aporta realmente código.  Por ejemplo, considere el siguiente código:  
  
```  
Line 5: // comment  
Line 6: x = 1;  
```  
  
 La línea 5 no contribuye ningún código al programa que se depura.  Si el depurador que establece el punto de interrupción en la línea 5 desea el OF para buscar hacia delante una cantidad determinada para la primera línea participante código, el depurador especificaría un intervalo que incluye líneas adicionales de candidato donde un punto de interrupción podría estar correctamente.  El A continuación buscaría hacia delante a través de las líneas hasta que encontrar una línea que puede aceptar un punto de interrupción.  
  
## Vea también  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)   
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md)