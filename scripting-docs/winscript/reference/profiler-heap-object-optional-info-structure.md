---
title: PROFILER_HEAP_OBJECT_OPTIONAL_INFO (estructura) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 77e638bd-ae36-4292-a170-90a0c500e610
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 52e231484b48bf2741281644c746b448fd6f657b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24734035"
---
# <a name="profilerheapobjectoptionalinfo-structure"></a>PROFILER_HEAP_OBJECT_OPTIONAL_INFO (Estructura)
Representa información opcional sobre objetos de montón.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef struct _PROFILER_HEAP_OBJECT_OPTIONAL_INFO{    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE infoType;    [switch_type(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE), switch_is(infoType)] union    {        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_PROTOTYPE)] PROFILER_HEAP_OBJECT_ID prototype;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_FUNCTION_NAME)] LPCWSTR functionName;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_ELEMENT_ATTRIBUTES_SIZE)] UINT elementAttributesSize;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_ELEMENT_TEXT_CHILDREN_SIZE)] UINT elementTextChildrenSize;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_SCOPE_LIST)] PROFILER_HEAP_OBJECT_SCOPE_LIST* scopeList;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_INTERNAL_PROPERTY)] PROFILER_HEAP_OBJECT_RELATIONSHIP* internalProperty;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_NAME_PROPERTIES)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* namePropertyList;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_INDEX_PROPERTIES)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* indexPropertyList;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_RELATIONSHIPS)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* relationshipList;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_WINRTEVENTS)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* eventList;    };} PROFILER_HEAP_OBJECT_OPTIONAL_INFO;  
```  
  
## <a name="members"></a>Miembros  
  
|Miembro|Tipo|Descripción|  
|------------|----------|-----------------|  
|Tipo de información|[PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE (Enumeración)](../../winscript/reference/profiler-heap-object-optional-info-type-enumeration.md)|El tipo de la información opcional.|  
|prototipo|[PROFILER_HEAP_OBJECT_ID (Tipo)](../../winscript/reference/profiler-heap-object-id-type.md)|El identificador de objeto de prototipo del objeto de montón.|  
|functionName|LPCWSTR|Nombre de la función del objeto de montón.|  
|elementAttributesSize|UINT|El tamaño de los atributos del elemento del objeto de montón.|  
|elementTextChildrenSize|UINT|El tamaño de los elementos secundarios de texto del objeto de montón.|  
|ListaÁmbito|[PROFILER_HEAP_OBJECT_SCOPE_LIST (Estructura)](../../winscript/reference/profiler-heap-object-scope-list-structure.md)|Lista de ámbito del objeto de montón.|  
|internalProperty|[PROFILER_HEAP_OBJECT_RELATIONSHIP (Estructura)](../../winscript/reference/profiler-heap-object-relationship-structure.md)|Propiedad interna del objeto de montón|  
|namePropertyList|[PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST (Estructura)](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Una lista de propiedades de nombre del objeto de montón.|  
|indexPropertyList|[PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST (Estructura)](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Una lista de propiedades del índice del objeto de montón.|  
|relationshipList|[PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST (Estructura)](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Una lista de las relaciones del objeto de montón.|  
|eventList|[PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST (Estructura)](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Una lista de eventos del objeto de montón.|