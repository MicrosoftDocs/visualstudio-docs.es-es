---
title: "IActiveScriptProfilerHeapEnum::GetOptionalInfo (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 99ed9df5-71cf-4c25-b189-af9accc466ee
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScriptProfilerHeapEnum::GetOptionalInfo (M&#233;todo)
Obtiene información opcional sobre el objeto especificado \(del conjunto de objetos de montón devueltos por [IActiveScriptProfilerControl3::EnumHeap \(Método\)](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)\).  
  
 No debe liberar la memoria asignada devuelta a los objetos devueltos.  En su lugar, debe llamar a [IActiveScriptProfilerHeapEnum::FreeObjectAndOptionalInfo \(Método\)](../../winscript/reference/iactivescriptprofilerheapenum-freeobjectandoptionalinfo-method.md).  
  
## Sintaxis  
  
```  
HRESULT GetOptionalInfo (  
    [in] PROFILER_HEAP_OBJECT* heapObject,  
    [in] ULONG celt,  
    [out, size_is(celt)] PROFILER_HEAP_OBJECT_OPTIONAL_INFO* optionalInfo);  
  
```  
  
#### Parámetros  
 `heapObject`  
 Objeto [PROFILER\_HEAP\_OBJECT \(Estructura\)](../../winscript/reference/profiler-heap-object-structure.md) para el que se va a devolver la información.  
  
 `celt`  
 Número de estructuras [PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO \(Estructura\)](../../winscript/reference/profiler-heap-object-optional-info-structure.md) que se van a devolver.  
  
 `optionalInfo`  
 \[out\] Matriz de estructuras [PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO \(Estructura\)](../../winscript/reference/profiler-heap-object-optional-info-structure.md) para el objeto especificado.  
  
## Valor devuelto  
 HRESULT.