---
title: PROFILER_HEAP_OBJECT (estructura) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 9f35362c-6856-4cfb-b990-031a156a58eb
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ad50f03806cbf98450c0fc917f1a97ca7305d05c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24734345"
---
# <a name="profilerheapobject-structure"></a>PROFILER_HEAP_OBJECT (Estructura)
Representa los objetos de montón recopilados por [método iactivescriptprofilercontrol3:: Enumheap](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef struct _PROFILER_HEAP_OBJECT  
{  
    UINT size;    union {        PROFILER_HEAP_OBJECT_ID objectId;        PROFILER_EXTERNAL_OBJECT_ADDRESS externalObjectAddress;    };    PROFILER_HEAP_OBJECT_NAME_ID typeNameId;    USHORT flags;     USHORT optionalInfoCount;} PROFILER_HEAP_OBJECT;  
```  
  
## <a name="members"></a>Miembros  
  
|Miembro|Tipo|Descripción|  
|------------|----------|-----------------|  
|objectId|[PROFILER_HEAP_OBJECT_ID (Tipo)](../../winscript/reference/profiler-heap-object-id-type.md)|Identificador del objeto de montón.|  
|externalObjectAddress|[PROFILER_EXTERNAL_OBJECT_ADDRESS (Tipo)](../../winscript/reference/profiler-external-object-address-type.md)|Dirección del objeto externo de un objeto, como un objeto asignado C++, que está fuera del montón de JavaScript.|  
|typeNameId|[PROFILER_HEAP_OBJECT_NAME_ID (Tipo)](../../winscript/reference/profiler-heap-object-name-id-type.md)|El identificador del nombre del tipo de objeto de montón, se recupera de [IActiveScriptProfilerHeapEnum::GetNameIdMap](../../winscript/reference/iactivescriptprofilerheapenum-getnameidmap.md). Solo uno de `externalObjectAddress` o `typeName` está presente en función de la `flags` valor.|  
|marcas|[PROFILER_HEAP_OBJECT_FLAGS (Enumeración)](../../winscript/reference/profiler-heap-object-flags-enumeration.md)|Las marcas que contienen información básica sobre el objeto de montón.|  
|optionalInfoCount|USHORT|El número de [PROFILER_HEAP_OBJECT_OPTIONAL_INFO (estructura)](../../winscript/reference/profiler-heap-object-optional-info-structure.md) registros que están disponibles para el objeto de montón.|