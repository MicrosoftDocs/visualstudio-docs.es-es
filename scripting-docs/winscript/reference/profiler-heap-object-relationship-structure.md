---
title: PROFILER_HEAP_OBJECT_RELATIONSHIP (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 3ab3d986-3314-4c7b-a1c8-18ed691a8b9c
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2b992b020c0aa42a6f27e484d55fe89a514c0198
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="profilerheapobjectrelationship-structure"></a>PROFILER_HEAP_OBJECT_RELATIONSHIP (Estructura)
Representa una relación de un objeto de montón.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef struct _PROFILER_HEAP_OBJECT_RELATIONSHIP{    PROFILER_HEAP_OBJECT_NAME_ID relationshipId;    PROFILER_RELATIONSHIP_INFO relationshipInfo;    [switch_type(PROFILER_RELATIONSHIP_INFO), switch_is(relationshipInfo)] union    {        [case(PROFILER_PROPERTY_TYPE_NUMBER)] double numberValue;        [case(PROFILER_PROPERTY_TYPE_STRING)] LPCWSTR stringValue;        [case(PROFILER_PROPERTY_TYPE_HEAP_OBJECT)] PROFILER_HEAP_OBJECT_ID objectId;        [case(PROFILER_PROPERTY_TYPE_EXTERNAL_OBJECT)] PROFILER_EXTERNAL_OBJECT_ADDRESS externalObjectAddress;    };} PROFILER_HEAP_OBJECT_RELATIONSHIP;  
```  
  
## <a name="members"></a>Miembros  
  
|Miembro|Valor|Descripción|  
|------------|-----------|-----------------|  
|relationshipId|[PROFILER_HEAP_OBJECT_NAME_ID (Tipo)](../../winscript/reference/profiler-heap-object-name-id-type.md)|El identificador de la relación de nombre de [IActiveScriptProfilerHeapEnum::GetNameIdMap](../../winscript/reference/iactivescriptprofilerheapenum-getnameidmap.md).|  
|relationshipInfo|[PROFILER_RELATIONSHIP_INFO (Enumeración)](../../winscript/reference/profiler-relationship-info-enumeration.md)|Información sobre la relación.|  
|numberValue|double|El valor del número. Solo uno de `numberValue` / `stringValue` / `objectId` / `externalObjectAddress` está establecido, tomando como base la `relationshipInfo` valor.|  
|StringValue|LPCWSTR|Valor de cadena.|  
|objectId|[PROFILER_HEAP_OBJECT_ID (Tipo)](../../winscript/reference/profiler-heap-object-id-type.md)|Identificador del objeto de montón.|  
|externalObjectAddress|[PROFILER_EXTERNAL_OBJECT_ADDRESS (Tipo)](../../winscript/reference/profiler-external-object-address-type.md)|La dirección del objeto externo.|  
|Subcadena|[PROFILER_PROPERTY_TYPE_SUBSTRING_INFO (Estructura)](../../winscript/reference/profiler-property-type-substring-info-structure.md)|La información sobre el tipo de la subcadena.|