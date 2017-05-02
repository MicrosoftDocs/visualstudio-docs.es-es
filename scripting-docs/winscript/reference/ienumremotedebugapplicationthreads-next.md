---
title: "IEnumRemoteDebugApplicationThreads::Next | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumRemoteDebugApplicationThreads.Next
apilocation: pdm.dll
helpviewer_keywords: 
  - "IEnumRemoteDebugApplicationThreads::Next"
ms.assetid: d8d10d7e-3468-49be-acf9-d842db9940e7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumRemoteDebugApplicationThreads::Next
El método de `Next` recupera un número especificado de segmentos de la secuencia de la enumeración.  
  
## Sintaxis  
  
```  
HRESULT Next(  
   ULONG                            celt,  
   IRemoteDebugApplicationThread**  pprdat,  
   ULONG*                           pceltFetched  
);  
```  
  
#### Parámetros  
 `celt`  
 \[in\] número de segmentos a recuperar.  
  
 `pprdat`  
 \[out\] devuelve una matriz de las interfaces de `IRemoteDebugApplicationThread` que representa los segmentos que se recuperan.  
  
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
 [IEnumRemoteDebugApplicationThreads \(Interfaz\)](../../winscript/reference/ienumremotedebugapplicationthreads-interface.md)