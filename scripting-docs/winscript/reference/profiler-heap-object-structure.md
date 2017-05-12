---
title: "PROFILER_HEAP_OBJECT (Estructura) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 9f35362c-6856-4cfb-b990-031a156a58eb
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# PROFILER_HEAP_OBJECT (Estructura)
Representa los objetos del montón recopilados por [IActiveScriptProfilerControl3::EnumHeap \(Método\)](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).  
  
## Sintaxis  
  
```  
typedef struct _PROFILER_HEAP_OBJECT  
{  
    UINT size;  
    union {  
        PROFILER_HEAP_OBJECT_ID objectId;  
        PROFILER_EXTERNAL_OBJECT_ADDRESS externalObjectAddress;  
    };  
    PROFILER_HEAP_OBJECT_NAME_ID typeNameId;  
    USHORT flags;   
    USHORT optionalInfoCount;  
} PROFILER_HEAP_OBJECT;  
```  
  
## Members  
  
|Miembro|Tipo|Descripción|  
|-------------|----------|-----------------|  
|objectId|[PROFILER\_HEAP\_OBJECT\_ID \(Tipo\)](../../winscript/reference/profiler-heap-object-id-type.md)|El id. de objeto de la pila.|  
|externalObjectAddress|[PROFILER\_EXTERNAL\_OBJECT\_ADDRESS \(Tipo\)](../../winscript/reference/profiler-external-object-address-type.md)|La dirección externa de objeto de un objeto, como objeto de C\+\+. \+\+\-allocated, que está fuera de la pila de JavaScript.|  
|typeNameId|[PROFILER\_HEAP\_OBJECT\_NAME\_ID \(Tipo\)](../../winscript/reference/profiler-heap-object-name-id-type.md)|El id. del nombre del tipo de objeto del montón, recuperado de [IActiveScriptProfilerHeapEnum::GetNameIdMap](../../winscript/reference/iactivescriptprofilerheapenum-getnameidmap.md).  Solo uno de `externalObjectAddress` o de `typeName` está presente según el valor de `flags` .|  
|Marcas|[PROFILER\_HEAP\_OBJECT\_FLAGS \(Enumeración\)](../../winscript/reference/profiler-heap-object-flags-enumeration.md)|Los indicadores que contienen información básica sobre el objeto de pila.|  
|optionalInfoCount|USHORT|El número de registros de [PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO \(Estructura\)](../../winscript/reference/profiler-heap-object-optional-info-structure.md) disponibles para el objeto de pila.|