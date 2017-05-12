---
title: "IActiveScriptProfilerHeapEnum::FreeObjectAndOptionalInfo (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: fdd5f7cc-be4e-4c13-a181-6320d26b44eb
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IActiveScriptProfilerHeapEnum::FreeObjectAndOptionalInfo (M&#233;todo)
Libera las estructuras especificadas de [PROFILER\_HEAP\_OBJECT \(Estructura\)](../../winscript/reference/profiler-heap-object-structure.md) y sus elementos asociados de [PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO \(Estructura\)](../../winscript/reference/profiler-heap-object-optional-info-structure.md) .  
  
## Sintaxis  
  
```  
HRESULT FreeObjectAndOptionalInfo (  
    [in] ULONG celt,  
    [in, size_is(celt)] PROFILER_HEAP_OBJECT** heapObjects);  
  
```  
  
#### Parámetros  
 `celt`  
 El número de objetos a liberar.  
  
 `heapObjects`  
 Matriz de estructuras [PROFILER\_HEAP\_OBJECT \(Estructura\)](../../winscript/reference/profiler-heap-object-structure.md).  
  
## Valor devuelto  
 HRESULT.