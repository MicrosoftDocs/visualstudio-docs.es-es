---
title: "PROFILER_HEAP_OBJECT_RELATIONSHIP (Estructura) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 3ab3d986-3314-4c7b-a1c8-18ed691a8b9c
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# PROFILER_HEAP_OBJECT_RELATIONSHIP (Estructura)
Representa una relación de un objeto de la pila.  
  
## Sintaxis  
  
```  
typedef struct _PROFILER_HEAP_OBJECT_RELATIONSHIP  
{  
    PROFILER_HEAP_OBJECT_NAME_ID relationshipId;  
    PROFILER_RELATIONSHIP_INFO relationshipInfo;  
    [switch_type(PROFILER_RELATIONSHIP_INFO), switch_is(relationshipInfo)] union  
    {  
        [case(PROFILER_PROPERTY_TYPE_NUMBER)] double numberValue;  
        [case(PROFILER_PROPERTY_TYPE_STRING)] LPCWSTR stringValue;  
        [case(PROFILER_PROPERTY_TYPE_HEAP_OBJECT)] PROFILER_HEAP_OBJECT_ID objectId;  
        [case(PROFILER_PROPERTY_TYPE_EXTERNAL_OBJECT)] PROFILER_EXTERNAL_OBJECT_ADDRESS externalObjectAddress;  
    };  
} PROFILER_HEAP_OBJECT_RELATIONSHIP;  
  
```  
  
## Members  
  
|Miembro|Valor|Descripción|  
|-------------|-----------|-----------------|  
|relationshipId|[PROFILER\_HEAP\_OBJECT\_NAME\_ID \(Tipo\)](../../winscript/reference/profiler-heap-object-name-id-type.md)|El id. del nombre de la relación, de [IActiveScriptProfilerHeapEnum::GetNameIdMap](../../winscript/reference/iactivescriptprofilerheapenum-getnameidmap.md).|  
|relationshipInfo|[PROFILER\_RELATIONSHIP\_INFO \(Enumeración\)](../../winscript/reference/profiler-relationship-info-enumeration.md)|Información sobre la relación.|  
|numberValue|double|El valor del número.  Solo uno de `numberValue`\/`stringValue`\/`objectId`\/`externalObjectAddress` se establece, según el valor de `relationshipInfo` .|  
|stringValue|LPCWSTR|Valor de cadena.|  
|objectId|[PROFILER\_HEAP\_OBJECT\_ID \(Tipo\)](../../winscript/reference/profiler-heap-object-id-type.md)|El id. de objeto de la pila.|  
|externalObjectAddress|[PROFILER\_EXTERNAL\_OBJECT\_ADDRESS \(Tipo\)](../../winscript/reference/profiler-external-object-address-type.md)|La dirección externa del objeto.|