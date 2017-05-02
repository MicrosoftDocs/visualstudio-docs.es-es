---
title: "PROFILER_HEAP_OBJECT_OPTIONAL_INFO (Estructura) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 77e638bd-ae36-4292-a170-90a0c500e610
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# PROFILER_HEAP_OBJECT_OPTIONAL_INFO (Estructura)
Representa la información opcional sobre los objetos del montón.  
  
## Sintaxis  
  
```  
typedef struct _PROFILER_HEAP_OBJECT_OPTIONAL_INFO  
{  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE infoType;  
    [switch_type(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE), switch_is(infoType)] union  
    {  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_PROTOTYPE)] PROFILER_HEAP_OBJECT_ID prototype;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_FUNCTION_NAME)] LPCWSTR functionName;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_ELEMENT_ATTRIBUTES_SIZE)] UINT elementAttributesSize;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_ELEMENT_TEXT_CHILDREN_SIZE)] UINT elementTextChildrenSize;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_SCOPE_LIST)] PROFILER_HEAP_OBJECT_SCOPE_LIST* scopeList;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_INTERNAL_PROPERTY)] PROFILER_HEAP_OBJECT_RELATIONSHIP* internalProperty;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_NAME_PROPERTIES)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* namePropertyList;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_INDEX_PROPERTIES)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* indexPropertyList;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_RELATIONSHIPS)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* relationshipList;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_WINRTEVENTS)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* eventList;  
    };  
} PROFILER_HEAP_OBJECT_OPTIONAL_INFO;  
  
```  
  
## Members  
  
|Miembro|Tipo|Descripción|  
|-------------|----------|-----------------|  
|infoType|[PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO\_TYPE \(Enumeración\)](../../winscript/reference/profiler-heap-object-optional-info-type-enumeration.md)|El tipo de información opcional.|  
|prototipo|[PROFILER\_HEAP\_OBJECT\_ID \(Tipo\)](../../winscript/reference/profiler-heap-object-id-type.md)|El id. del objeto prototype del objeto de pila.|  
|`functionName`|LPCWSTR|El nombre de la función del objeto de pila.|  
|elementAttributesSize|UINT|El tamaño de los atributos del elemento de objeto del montón.|  
|elementTextChildrenSize|UINT|El tamaño de los elementos secundarios del texto del objeto de pila.|  
|scopeList|[PROFILER\_HEAP\_OBJECT\_SCOPE\_LIST \(Estructura\)](../../winscript/reference/profiler-heap-object-scope-list-structure.md)|La lista del ámbito del objeto de pila.|  
|internalProperty|[PROFILER\_HEAP\_OBJECT\_RELATIONSHIP \(Estructura\)](../../winscript/reference/profiler-heap-object-relationship-structure.md)|La propiedad interna del objeto de pila.|  
|namePropertyList|[PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_LIST \(Estructura\)](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Una lista de las propiedades de nombre de objeto del montón.|  
|indexPropertyList|[PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_LIST \(Estructura\)](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Una lista de las propiedades del índice del objeto de pila.|  
|relationshipList|[PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_LIST \(Estructura\)](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Una lista de las relaciones de objeto de la pila.|  
|eventList|[PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_LIST \(Estructura\)](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Una lista de los eventos del objeto de pila.|