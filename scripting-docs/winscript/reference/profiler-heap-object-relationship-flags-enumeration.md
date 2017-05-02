---
title: "PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS (Enumeraci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 1a41b642-c9a9-4d83-b943-d59b232eebf6
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS (Enumeraci&#243;n)
Marcas que representan si un objeto de montón designado en una relación de objeto es un método get o set.  Se utiliza en el método [EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md) cuando el valor de PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_FLAGS se especifica en el parámetro `enumFlags` .  
  
## Sintaxis  
  
```  
typedef [v1_enum] enum {  
    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_NONE                      = 0x00000000,  
    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_GET_ACCESSOR           = 0x00010000,  
    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_SET_ACCESSOR           = 0x00020000,  
} PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS;  
  
```  
  
## Members  
  
|Miembro|Valor|Descripción|  
|-------------|-----------|-----------------|  
|PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_FLAGS\_NONE|0x00000000|Este objeto de pila designado en una relación del objeto no se identifica como un método get o método set.|  
|PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_FLAGS\_IS\_GET\_ACCESSOR|0x00010000|El objeto de montón designado en una relación de objeto es un método Get.  Esta información se almacenará en el alto 2 bytes \(16 bits\) del campo [PROFILER\_HEAP\_OBJECT\_RELATIONSHIP.relationshipInfo](../../winscript/reference/profiler-heap-object-relationship-structure.md) .|  
|PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_FLAGS\_IS\_SET\_ACCESSOR|0x00020000|El objeto de montón designado en una relación de objeto es un método Set.  Esta información se almacenará en el alto 2 bytes \(16 bits\) del campo `PROFILER_HEAP_OBJECT_RELATIONSHIP.relationshipInfo` .|