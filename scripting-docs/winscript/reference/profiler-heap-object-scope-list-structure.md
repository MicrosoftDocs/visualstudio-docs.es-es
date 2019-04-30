---
title: PROFILER_HEAP_OBJECT_SCOPE_LIST (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 33ebaa31-0a35-47d5-a4e3-afd83e16f53e
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b1285e4efa3db8a7ec99808f5888d3dbf948e589
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62830326"
---
# <a name="profilerheapobjectscopelist-structure"></a>PROFILER_HEAP_OBJECT_SCOPE_LIST (Estructura)
Esta estructura solo se asocia a objetos de función. La lista de ámbitos representa el cierre de la función como una lista de ámbitos donde cada ámbito es un objeto de montón con una lista de propiedades asociada que representa variables en cada ámbito determinado. En algunos casos, los nombres de los objetos de ámbito no esté disponible y solo su índice en la lista de propiedades está disponible.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
typedef struct _PROFILER_HEAP_OBJECT_SCOPE_LIST{    UINT count;    [size_is(count)] PROFILER_HEAP_OBJECT_ID scopes[];} PROFILER_HEAP_OBJECT_SCOPE_LIST;  
```  
  
## <a name="members"></a>Miembros  
  
|Miembro|Tipo|Descripción|  
|------------|----------|-----------------|  
|count|UINT|El número de ámbitos|  
|scopes|[PROFILER_HEAP_OBJECT_ID (Tipo)](../../winscript/reference/profiler-heap-object-id-type.md)|Una matriz de ámbitos.|