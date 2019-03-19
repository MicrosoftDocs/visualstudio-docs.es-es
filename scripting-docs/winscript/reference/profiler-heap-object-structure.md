---
title: PROFILER_HEAP_OBJECT (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 9f35362c-6856-4cfb-b990-031a156a58eb
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a1652c6ebffff88782ffcc879158a5142f22395d
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58151198"
---
# <a name="profilerheapobject-structure"></a>PROFILER_HEAP_OBJECT (Estructura)
Representa los objetos del montón recopilados por [Iactivescriptprofilercontrol3 método](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
typedef struct _PROFILER_HEAP_OBJECT  
{  
    UINT size;    union {        PROFILER_HEAP_OBJECT_ID objectId;        PROFILER_EXTERNAL_OBJECT_ADDRESS externalObjectAddress;    };    PROFILER_HEAP_OBJECT_NAME_ID typeNameId;    USHORT flags;     USHORT optionalInfoCount;} PROFILER_HEAP_OBJECT;  
```  
  
## <a name="members"></a>Miembros  
  
|Miembro|Tipo|Descripción|  
|------------|----------|-----------------|  
|objectId|[PROFILER_HEAP_OBJECT_ID (Tipo)](../../winscript/reference/profiler-heap-object-id-type.md)|Identificador del objeto de montón.|  
|externalObjectAddress|[PROFILER_EXTERNAL_OBJECT_ADDRESS (Tipo)](../../winscript/reference/profiler-external-object-address-type.md)|La dirección del objeto externo de un objeto, como un objeto asignado en C++, que está fuera del montón de JavaScript.|  
|typeNameId|[PROFILER_HEAP_OBJECT_NAME_ID (Tipo)](../../winscript/reference/profiler-heap-object-name-id-type.md)|El identificador del nombre del tipo de objeto de montón, se recuperan de [IActiveScriptProfilerHeapEnum::GetNameIdMap](../../winscript/reference/iactivescriptprofilerheapenum-getnameidmap.md). Solo uno de `externalObjectAddress` o `typeName` está presente en función de la `flags` valor.|  
|marcas|[PROFILER_HEAP_OBJECT_FLAGS (Enumeración)](../../winscript/reference/profiler-heap-object-flags-enumeration.md)|Las marcas que contienen información básica sobre el objeto de montón.|  
|optionalInfoCount|USHORT|El número de [PROFILER_HEAP_OBJECT_OPTIONAL_INFO (estructura)](../../winscript/reference/profiler-heap-object-optional-info-structure.md) registros que están disponibles para el objeto de montón.|