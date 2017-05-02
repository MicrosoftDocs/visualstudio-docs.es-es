---
title: "IActiveScriptProfilerHeapEnum (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 16756d0e-547a-4825-8b7b-a7e0e4708a04
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScriptProfilerHeapEnum (Interfaz)
Un iterador sobre los objetos del montón asociados a un motor de script, recopilado por [IActiveScriptProfilerControl3::EnumHeap \(Método\)](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).  
  
## Sintaxis  
  
```vb  
interface IActiveScriptProfilerHeapEnum : IUnknown  
```  
  
## Métodos  
 [IActiveScriptProfilerHeapEnum::Next Method](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md)  
 Obtiene el objeto o los objetos siguientes en el conjunto de objetos del montón recopilados por [IActiveScriptProfilerControl3::EnumHeap \(Método\)](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).  
  
 [IActiveScriptProfilerHeapEnum::GetOptionalInfo \(Método\)](../../winscript/reference/iactivescriptprofilerheapenum-getoptionalinfo-method.md)  
 Obtiene la información opcional en el objeto especificado en el conjunto de objetos del montón recopilados por [IActiveScriptProfilerControl3::EnumHeap \(Método\)](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).  
  
 [IActiveScriptProfilerHeapEnum::FreeObjectAndOptionalInfo \(Método\)](../../winscript/reference/iactivescriptprofilerheapenum-freeobjectandoptionalinfo-method.md)  
 Libera las estructuras especificadas de [PROFILER\_HEAP\_OBJECT \(Estructura\)](../../winscript/reference/profiler-heap-object-structure.md) y sus elementos asociados de [PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO \(Estructura\)](../../winscript/reference/profiler-heap-object-optional-info-structure.md) .  
  
 [IActiveScriptProfilerHeapEnum::GetNameIdMap](../../winscript/reference/iactivescriptprofilerheapenum-getnameidmap.md)  
 Devuelve los nombres de cadena correspondiente a los valores de [PROFILER\_HEAP\_OBJECT\_NAME\_ID \(Tipo\)](../../winscript/reference/profiler-heap-object-name-id-type.md) .