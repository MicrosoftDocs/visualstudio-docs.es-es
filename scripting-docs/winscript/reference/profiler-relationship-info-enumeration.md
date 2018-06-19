---
title: PROFILER_RELATIONSHIP_INFO (enumeración) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: fae69317-6224-4a6a-8e9e-ccaa6a330818
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f01ca5e001d45907af70b46b6dc362e8ae0b2044
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24733935"
---
# <a name="profilerrelationshipinfo-enumeration"></a>PROFILER_RELATIONSHIP_INFO (Enumeración)
Representa información sobre el objeto en la relación. Usar en [PROFILER_HEAP_OBJECT_RELATIONSHIP (estructura)](../../winscript/reference/profiler-heap-object-relationship-structure.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef [v1_enum] enum {    PROFILER_PROPERTY_TYPE_NUMBER = 0x01,    PROFILER_PROPERTY_TYPE_STRING = 0x02,    PROFILER_PROPERTY_TYPE_HEAP_OBJECT = 0x03,    PROFILER_PROPERTY_TYPE_EXTERNAL_OBJECT = 0x04,    PROFILER_PROPERTY_TYPE_BSTR = 0x05,} PROFILER_RELATIONSHIP_INFO;  
```  
  
## <a name="members"></a>Miembros  
  
|Miembro|Valor|Descripción|  
|------------|-----------|-----------------|  
|PROFILER_PROPERTY_TYPE_NUMBER|0 x 01|El objeto es un número.|  
|PROFILER_PROPERTY_TYPE_STRING|0 x 02|El objeto es una cadena.|  
|PROFILER_PROPERTY_TYPE_HEAP_OBJECT|0 x 03|El objeto es un objeto de montón.|  
|PROFILER_PROPERTY_TYPE_EXTERNAL_OBJECT|0 x 04|El objeto es externo, es decir, no en el montón de elementos no utilizados.|  
|PROFILER_PROPERTY_TYPE_BSTR|0 x 05|El objeto es una cadena BSTR.|  
|PROFILER_PROPERTY_TYPE_SUBSTRING|0 x 06|El objeto es una SUBCADENA.|