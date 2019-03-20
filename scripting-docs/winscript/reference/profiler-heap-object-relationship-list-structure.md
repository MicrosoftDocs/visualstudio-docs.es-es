---
title: PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 46ca87ea-5b0f-437d-a33f-b2d9a457e036
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 23c6ee5f8ff4d7a8a19c19bae55bb72eb5c8fd06
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58155646"
---
# <a name="profilerheapobjectrelationshiplist-structure"></a>PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST (Estructura)
Representa una lista de relaciones que pertenecen a un objeto de montón.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
typedef struct _PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST{    UINT count;    [size_is(count)] PROFILER_HEAP_OBJECT_RELATIONSHIP elements[];} PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST;  
```  
  
## <a name="members"></a>Miembros  
  
|Miembro|Tipo|Descripción|  
|------------|----------|-----------------|  
|count|UINT|El número de relaciones de un objeto de montón.|  
|elementos|[PROFILER_HEAP_OBJECT_RELATIONSHIP (Estructura)](../../winscript/reference/profiler-heap-object-relationship-structure.md)|Las relaciones de un objeto de montón.|