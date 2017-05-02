---
title: "IEnumDebugApplicationNodes::Next | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugApplicationNodes.Next
apilocation: pdm.dll
helpviewer_keywords: 
  - "IEnumDebugApplicationNodes::Next"
ms.assetid: 925511c8-4f11-423d-ba2d-01589457050c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugApplicationNodes::Next
Recupera un número especificado de segmentos de la secuencia de la enumeración.  
  
## Sintaxis  
  
```  
HRESULT Next(  
   ULONG                    celt,  
   IDebugApplicationNode**  pprddp,  
   ULONG*                   pceltFetched  
);  
```  
  
#### Parámetros  
 `celt`  
 \[in\] número de segmentos a recuperar.  
  
 `pprddp`  
 \[out\] devuelve una matriz de las interfaces de `IDebugApplicationNode` que representa los segmentos que se recuperan.  
  
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
 [IEnumDebugApplicationNodes \(Interfaz\)](../../winscript/reference/ienumdebugapplicationnodes-interface.md)