---
title: PROFILER_HEAP_OBJECT_RELATIONSHIP (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 3ab3d986-3314-4c7b-a1c8-18ed691a8b9c
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7e5658f70e6a24151af75f4455fc44c2c756b9e9
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091954"
---
# <a name="profilerheapobjectrelationship-structure"></a>PROFILER_HEAP_OBJECT_RELATIONSHIP (Estructura)
Representa una relación de un objeto de montón.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
typedef struct _PROFILER_HEAP_OBJECT_RELATIONSHIP{    PROFILER_HEAP_OBJECT_NAME_ID relationshipId;    PROFILER_RELATIONSHIP_INFO relationshipInfo;    [switch_type(PROFILER_RELATIONSHIP_INFO), switch_is(relationshipInfo)] union    {        [case(PROFILER_PROPERTY_TYPE_NUMBER)] double numberValue;        [case(PROFILER_PROPERTY_TYPE_STRING)] LPCWSTR stringValue;        [case(PROFILER_PROPERTY_TYPE_HEAP_OBJECT)] PROFILER_HEAP_OBJECT_ID objectId;        [case(PROFILER_PROPERTY_TYPE_EXTERNAL_OBJECT)] PROFILER_EXTERNAL_OBJECT_ADDRESS externalObjectAddress;    };} PROFILER_HEAP_OBJECT_RELATIONSHIP;  
```  
  
## <a name="members"></a>Miembros  
  
|Miembro|Valor|Descripción|  
|------------|-----------|-----------------|  
|relationshipId|[PROFILER_HEAP_OBJECT_NAME_ID (Tipo)](../../winscript/reference/profiler-heap-object-name-id-type.md)|Identificador de la relación de nombre de [IActiveScriptProfilerHeapEnum::GetNameIdMap](../../winscript/reference/iactivescriptprofilerheapenum-getnameidmap.md).|  
|relationshipInfo|[PROFILER_RELATIONSHIP_INFO (Enumeración)](../../winscript/reference/profiler-relationship-info-enumeration.md)|Información sobre la relación.|  
|numberValue|double|El valor del número. Solo uno de `numberValue` / `stringValue` / `objectId` / `externalObjectAddress` está establecido, según la `relationshipInfo` valor.|  
|stringValue|LPCWSTR|Valor de cadena.|  
|Id. de objeto|[PROFILER_HEAP_OBJECT_ID (Tipo)](../../winscript/reference/profiler-heap-object-id-type.md)|Identificador del objeto de montón.|  
|externalObjectAddress|[PROFILER_EXTERNAL_OBJECT_ADDRESS (Tipo)](../../winscript/reference/profiler-external-object-address-type.md)|La dirección del objeto externo.|  
|Subcadena|[PROFILER_PROPERTY_TYPE_SUBSTRING_INFO (Estructura)](../../winscript/reference/profiler-property-type-substring-info-structure.md)|La información sobre el tipo de la subcadena.|