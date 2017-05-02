---
title: "PROFILER_HEAP_ENUM_FLAGS (Enumeraci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 17936b7a-40d5-4774-b92b-b24ee391591e
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# PROFILER_HEAP_ENUM_FLAGS (Enumeraci&#243;n)
Marcas que representan si se expone información adicional sobre un objeto de montón designado en una relación de objeto.  Se utiliza en el método [EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md) .  
  
## Sintaxis  
  
```  
typedef [v1_enum] enum {  
    PROFILER_HEAP_ENUM_FLAGS_NONE                      = 0x00000000,  
    PROFILER_HEAP_ENUM_FLAGS_STORE_RELATIONSHIP_FLAGS  = 0x00000001,  
} PROFILER_HEAP_ENUM_FLAGS;  
  
```  
  
## Members  
  
|Miembro|Valor|Descripción|  
|-------------|-----------|-----------------|  
|PROFILER\_HEAP\_ENUM\_FLAGS\_NONE|0x00000000|Este objeto de pila no expone la información adicional sobre una relación del objeto.  Este objeto de pila se comporta igual que [IActiveScriptProfilerControl3::HeapEnum](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).|  
|PROFILER\_HEAP\_ENUM\_ENUM\_ STORE\_RELATIONSHIP\_FLAGS|0x00000001|Este objeto de pila expone información sobre si un objeto designado en una relación de objeto es un método get o set.  Esta información se almacenará en el alto 2 bytes \(16 bits\) de campo [PROFILER\_HEAP\_OBJECT\_RELATIONSHIP.relationshipInfo](../../winscript/reference/profiler-heap-object-relationship-structure.md) como uno de los valores de enumeración [PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_FLAGS](../../winscript/reference/profiler-heap-object-relationship-flags-enumeration.md) .|