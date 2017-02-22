---
title: "IDebugDocumentPositionOffset2::GetRange | Microsoft Docs"
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
  - "IDebugDocumentPositionOffset2::GetRange"
ms.assetid: 27da7130-0932-4f97-abde-05e6fb018606
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDocumentPositionOffset2::GetRange
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Recupera el intervalo para la posición del documento actual.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetRange(  
   DWORD* pdwBegOffset,  
   DWORD* pdwEndOffset  
);  
```  
  
```c#  
public int GetRange(  
   ref uint pdwBegOffset,  
   ref uint pdwEndOffset  
);  
```  
  
#### Parámetros  
 `pdwBegOffset`  
 \[in, out\]  De para la posición inicial del intervalo.  Establezca este parámetro en un valor nulo si esta información no es necesaria.  
  
 `pdwEndOffset`  
 \[in, out\]  De para la posición final del intervalo.  Establezca este parámetro en un valor nulo si esta información no es necesaria.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 El intervalo especificado en una posición del documento para un punto de interrupción de ubicación es utilizado por el motor de depuración \(DE\) para buscar a continuación para una instrucción que aporta realmente código.  Por ejemplo, considere el siguiente código:  
  
```  
Line 5: // comment  
Line 6: x = 1;  
```  
  
 La línea 5 no contribuye ningún código al programa que se depura.  Si el depurador que establece el punto de interrupción en la línea 5 desea el OF para buscar hacia delante una cantidad determinada para la primera línea participante código, el depurador especificaría un intervalo que incluye líneas adicionales de candidato donde un punto de interrupción podría correctamente estar.  El A continuación buscaría hacia delante a través de las líneas hasta que encontrar una línea que puede aceptar un punto de interrupción.  
  
## Vea también  
 [IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)   
 [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)