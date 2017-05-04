---
title: "IActiveScriptProfilerHeapEnum::GetNameIdMap | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 88514c93-850b-48d4-9a68-1e27d7411f0d
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IActiveScriptProfilerHeapEnum::GetNameIdMap
Devuelve los nombres de cadena correspondiente a los valores de [PROFILER\_HEAP\_OBJECT\_NAME\_ID \(Tipo\)](../../winscript/reference/profiler-heap-object-name-id-type.md) .  
  
## Sintaxis  
  
```  
HRESULT GetNameIdMap (  
    [out, size_is(,*pcelt)] LPCWSTR* pNameList[],   
    [out] UINT *pcelt);  
```  
  
#### Parámetros  
 `pNameList`  
 \[out\] matriz de nombres asociados a los valores de [PROFILER\_HEAP\_OBJECT\_NAME\_ID \(Tipo\)](../../winscript/reference/profiler-heap-object-name-id-type.md) .  
  
 `pcelt`  
 \[out\] número de nombres de la matriz.  
  
## Valor devuelto  
 HRESULT.