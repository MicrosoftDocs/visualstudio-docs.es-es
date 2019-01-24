---
title: PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS (enumeración) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 1a41b642-c9a9-4d83-b943-d59b232eebf6
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b78285f332b339533d81228de5877043f699a67c
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349145"
---
# <a name="profilerheapobjectrelationshipflags-enumeration"></a>PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS (Enumeración)
Marcas que representan si un objeto de montón designado en una relación de objeto es un método de captador o establecedor. Utilizado en el [EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md) método cuando el valor PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS se especifica en el `enumFlags` parámetro.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
typedef [v1_enum] enum {    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_NONE                      = 0x00000000,    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_GET_ACCESSOR           = 0x00010000,    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_SET_ACCESSOR           = 0x00020000,} PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS;  
```  
  
## <a name="members"></a>Miembros  
  
|Miembro|Valor|Descripción|  
|------------|-----------|-----------------|  
|PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_NONE|0x00000000|Este objeto de montón designado en una relación de objeto no se identifica como método de captador o establecedor.|  
|PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_GET_ACCESSOR|0x00010000|El objeto de montón designado en una relación de objeto es un método de captador. Esta información se almacenará en los 2 bytes (16 bits) de la [PROFILER_HEAP_OBJECT_RELATIONSHIP.relationshipInfo](../../winscript/reference/profiler-heap-object-relationship-structure.md) campo.|  
|PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_SET_ACCESSOR|0x00020000|El objeto de montón designado en una relación de objeto es un método establecedor. Esta información se almacenará en los 2 bytes (16 bits) de la `PROFILER_HEAP_OBJECT_RELATIONSHIP.relationshipInfo` campo.|