---
title: "IEnumDebugCodeContexts::Next | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugCodeContexts.Next
apilocation: jscript.dll
helpviewer_keywords: 
  - "IEnumDebugCodeContexts::Next"
ms.assetid: 844cc353-ae0b-45e1-84a6-32b0bb67f57f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugCodeContexts::Next
Recupera un número especificado de segmentos de la secuencia de la enumeración.  
  
## Sintaxis  
  
```  
HRESULT Next(  
   ULONG                celt,  
   IDebugCodeContext**  pscc,  
   ULONG*               pceltFetched  
);  
```  
  
#### Parámetros  
 `celt`  
 \[in\] número de segmentos a recuperar.  
  
 `pscc`  
 \[out\] devuelve una matriz de las interfaces de `IDebugCodeContext` que representa los segmentos que se recuperan.  
  
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
 [IEnumDebugCodeContexts \(Interfaz\)](../../winscript/reference/ienumdebugcodecontexts-interface.md)