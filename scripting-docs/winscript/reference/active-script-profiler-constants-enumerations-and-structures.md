---
title: Active Script Profiler constantes, enumeraciones y estructuras | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 6e079d84-9dde-46fc-8a6a-18e902f60ecc
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a37f64b14d0d732e48de66bb5268d47c95426937
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="active-script-profiler-constants-enumerations-and-structures"></a>Active Script Profiler (Constantes, enumeraciones y estructuras)
Active Script Profiler Interfaces utiliza las enumeraciones siguientes.  
  
## <a name="constants-enumerations-and-structures"></a>Constantes, enumeraciones y estructuras  
  
|Constantes|Descripción|  
|---------------|-----------------|  
|[PROFILER_EXTERNAL_OBJECT_ADDRESS (Tipo)](../../winscript/reference/profiler-external-object-address-type.md)|Dirección del objeto externo del generador de perfiles. Usar en [PROFILER_HEAP_OBJECT (estructura)](../../winscript/reference/profiler-heap-object-structure.md) y [PROFILER_HEAP_OBJECT_RELATIONSHIP (estructura)](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|[PROFILER_HEAP_OBJECT_ID (Tipo)](../../winscript/reference/profiler-heap-object-id-type.md)|Identificador del objeto de montón. Usar en [PROFILER_HEAP_OBJECT (estructura)](../../winscript/reference/profiler-heap-object-structure.md)[PROFILER_HEAP_OBJECT_SCOPE_LIST (estructura)](../../winscript/reference/profiler-heap-object-scope-list-structure.md), [PROFILER_HEAP_OBJECT_OPTIONAL_INFO (estructura)](../../winscript/reference/profiler-heap-object-optional-info-structure.md)y [PROFILER_HEAP_OBJECT_RELATIONSHIP (estructura)](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|[PROFILER_HEAP_OBJECT_NAME_ID (Tipo)](../../winscript/reference/profiler-heap-object-name-id-type.md)|Identificador del nombre del objeto de montón. Usar en [PROFILER_HEAP_OBJECT (estructura)](../../winscript/reference/profiler-heap-object-structure.md).|  
  
|Enumeraciones|Descripción|  
|------------------|-----------------|  
|[PROFILER_EVENT_MASK (Enumeración)](../../winscript/reference/profiler-event-mask-enumeration.md)|Indica los tipos de eventos de los que se deben generar perfiles.|  
|[PROFILER_HEAP_ENUM_FLAGS (Enumeración)](../../winscript/reference/profiler-heap-enum-flags-enumeration.md)|Marcas que representan si se expone información adicional sobre un objeto de montón al que se apunta en una relación de objeto. Utilizado en el [método iactivescriptprofilercontrol5:: Enumheap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md).|  
|[PROFILER_HEAP_OBJECT_FLAGS (Enumeración)](../../winscript/reference/profiler-heap-object-flags-enumeration.md)|Marcas que representan información básica sobre el objeto de montón. Utilizado en el [PROFILER_HEAP_OBJECT (estructura)](../../winscript/reference/profiler-heap-object-structure.md).|  
|[PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE (Enumeración)](../../winscript/reference/profiler-heap-object-optional-info-type-enumeration.md)|Representa distintos tipos de información opcional. Usar en [PROFILER_HEAP_OBJECT_OPTIONAL_INFO (estructura)](../../winscript/reference/profiler-heap-object-optional-info-structure.md).|  
|[PROFILER_RELATIONSHIP_INFO (Enumeración)](../../winscript/reference/profiler-relationship-info-enumeration.md)|Representa información sobre el objeto en la relación. Usar en [PROFILER_HEAP_OBJECT_RELATIONSHIP (estructura)](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|[PROFILER_SCRIPT_TYPE (Enumeración)](../../winscript/reference/profiler-script-type-enumeration.md)|Especifica el tipo de script.|  
  
|Estructuras|Descripción|  
|----------------|-----------------|  
|[PROFILER_HEAP_OBJECT (Estructura)](../../winscript/reference/profiler-heap-object-structure.md)|Representa los objetos de montón recopilados por [método iactivescriptprofilercontrol3:: Enumheap](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).|  
|[PROFILER_HEAP_OBJECT_OPTIONAL_INFO (Estructura)](../../winscript/reference/profiler-heap-object-optional-info-structure.md)|Representa información opcional sobre objetos de montón.|  
|[PROFILER_HEAP_OBJECT_RELATIONSHIP (Estructura)](../../winscript/reference/profiler-heap-object-relationship-structure.md)|Representa una relación de un objeto de montón.|  
|[PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST (Estructura)](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Representa una lista de relaciones que pertenecen a un objeto de montón.|  
|[PROFILER_HEAP_OBJECT_SCOPE_LIST (Estructura)](../../winscript/reference/profiler-heap-object-scope-list-structure.md)|Esta estructura solo se asocia a objetos de función. La lista de ámbitos representa el cierre de la función como una lista de ámbitos donde cada ámbito es un objeto de montón con una lista de propiedades asociada que representa variables en cada ámbito determinado. En algunos casos, puede que los nombres de los objetos de ese ámbito no estén disponibles; solo están disponibles sus identificadores.|  
|[PROFILER_PROPERTY_TYPE_SUBSTRING_INFO (Estructura)](../../winscript/reference/profiler-property-type-substring-info-structure.md)|Representa información sobre el tipo de la subcadena.|  
  
## <a name="see-also"></a>Vea también  
 [Active Script Profiler (Interfaces)](../../winscript/reference/active-script-profiler-interfaces.md)