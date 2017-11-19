---
title: "PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS (enumeración) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 1a41b642-c9a9-4d83-b943-d59b232eebf6
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ab542225e0238dbd40f90d9de66d43d0791e05e0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="profilerheapobjectrelationshipflags-enumeration"></a>PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS (Enumeración)
Marcas que representan si un objeto de montón que se apunta en una relación de objeto es un método de captador o un establecedor. Utilizado en el [EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md) método cuando se especifica el valor PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS en el `enumFlags` parámetro.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef [v1_enum] enum {    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_NONE                      = 0x00000000,    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_GET_ACCESSOR           = 0x00010000,    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_SET_ACCESSOR           = 0x00020000,} PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS;  
```  
  
## <a name="members"></a>Miembros  
  
|Miembro|Valor|Descripción|  
|------------|-----------|-----------------|  
|PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_NONE|0x00000000|Este objeto de montón que se apunta en una relación de objeto no se identifica como método de un captador o un establecedor.|  
|PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_GET_ACCESSOR|0x00010000|El objeto de montón que se apunta en una relación de objeto es un método de captador. Esta información se almacenará en la alta 2 bytes (16 bits) de la [PROFILER_HEAP_OBJECT_RELATIONSHIP.relationshipInfo](../../winscript/reference/profiler-heap-object-relationship-structure.md) campo.|  
|PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_SET_ACCESSOR|0x00020000|El objeto de montón que se apunta en una relación de objeto es un método de establecedor. Esta información se almacenará en la alta 2 bytes (16 bits) de la `PROFILER_HEAP_OBJECT_RELATIONSHIP.relationshipInfo` campo.|