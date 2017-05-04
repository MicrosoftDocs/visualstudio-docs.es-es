---
title: "PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE (Enumeraci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: fcb55f5f-ce75-4d05-9ce9-ba28c622f97d
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE (Enumeraci&#243;n)
Representa tipos diferentes de información opcional.  Utilizado en [PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO \(Estructura\)](../../winscript/reference/profiler-heap-object-optional-info-structure.md).  
  
## Sintaxis  
  
```  
typedef [v1_enum] enum {  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_PROTOTYPE                    = 0x00000001,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_FUNCTION_NAME                = 0x00000002,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_SCOPE_LIST                   = 0x00000003,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_INTERNAL_PROPERTY            = 0x00000004,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_NAME_PROPERTIES              = 0x00000005,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_INDEX_PROPERTIES             = 0x00000006,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_ELEMENT_ATTRIBUTES_SIZE      = 0x00000007,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_ELEMENT_TEXT_CHILDREN_SIZE   = 0x00000008,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_RELATIONSHIPS                = 0x00000009,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_WINRTEVENTS                  = 0x0000000A,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_MAX_VALUE                    = PROFILER_HEAP_OBJECT_OPTIONAL_INFO_WINRTEVENTS  
} PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE;  
  
```  
  
## Members  
  
|Miembro|Valor|Descripción|  
|-------------|-----------|-----------------|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFORMATION\_PROTOTYPE|0x00000001|Información sobre el prototipo del objeto de pila.|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFORMATION\_FUNCTION\_NAME|0x00000002|Información sobre el nombre de la función del objeto de pila.|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFORMATION\_SCOPE\_LIST|0x00000003|Información sobre [PROFILER\_HEAP\_OBJECT\_SCOPE\_LIST \(Estructura\)](../../winscript/reference/profiler-heap-object-scope-list-structure.md)de objeto de la pila.|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFORMATION\_INTERNAL\_PROPERTY|0x00000004|Información sobre la propiedad interna del objeto de pila.|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFORMATION\_NAME\_PROPERTIES|0x00000005|Información sobre las propiedades de nombre de objeto del montón.|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFORMATION\_INDEX\_PROPERTIES|0x00000006|Información sobre las propiedades del índice del objeto de pila.|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFORMATION\_ELEMENT\_ATTRIBUTES\_SIZE|0x00000007|El tamaño de los atributos asociados a un elemento DOM.|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFORMATION\_ELEMENT\_TEXT\_CHILDREN\_SIZE|0x00000008|El tamaño de cualquier texto que está asociado a un elemento DOM.|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFORMATION\_RELATIONSHIPS|0x00000009|Información sobre las relaciones de objeto de la pila.|  
|ROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFORMATION\_WINRTEVENTS|0x0000000A|Información sobre los eventos en tiempo de ejecución de Windows del objeto de pila.|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFORMATION\_MAX\_VALUE|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFORMATION\_WINRTEVENTS|El valor máximo de esta enumeración.|