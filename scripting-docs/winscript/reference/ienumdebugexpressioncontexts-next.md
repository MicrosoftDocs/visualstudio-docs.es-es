---
title: "IEnumDebugExpressionContexts::Next | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugExpressionContexts.Next
apilocation: jscript.dll
helpviewer_keywords: 
  - "IEnumDebugExpressionContexts::Next"
ms.assetid: aa223b0b-f7c1-4368-a59e-677e60133baf
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugExpressionContexts::Next
Recupera un número especificado de segmentos de la secuencia de la enumeración.  
  
## Sintaxis  
  
```  
HRESULT Next(  
   ULONG                      celt,  
   IDebugExpressionContext**  ppdec,  
   ULONG*                     pceltFetched  
);  
```  
  
#### Parámetros  
 `celt`  
 \[in\] número de segmentos a recuperar.  
  
 `ppdec`  
 \[out\] devuelve una matriz de las interfaces de `IDebugExpressionContext` que representa los segmentos que se recuperan.  
  
 `pceltFetched`  
 \[out\] número real de segmentos capturados por el enumerador.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Este método recupera un número especificado de segmentos de la secuencia de la enumeración.  
  
## Vea también  
 [IEnumDebugExpressionContexts \(Interfaz\)](../../winscript/reference/ienumdebugexpressioncontexts-interface.md)