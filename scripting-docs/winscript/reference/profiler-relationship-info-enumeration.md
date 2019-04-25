---
title: PROFILER_RELATIONSHIP_INFO (enumeración) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: fae69317-6224-4a6a-8e9e-ccaa6a330818
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0aa0a94668d06f75b959de2ee933ab079feba596
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58148118"
---
# <a name="profilerrelationshipinfo-enumeration"></a>PROFILER_RELATIONSHIP_INFO (Enumeración)
Representa información sobre el objeto en la relación. Utilizado en [PROFILER_HEAP_OBJECT_RELATIONSHIP (estructura)](../../winscript/reference/profiler-heap-object-relationship-structure.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
typedef [v1_enum] enum {    PROFILER_PROPERTY_TYPE_NUMBER = 0x01,    PROFILER_PROPERTY_TYPE_STRING = 0x02,    PROFILER_PROPERTY_TYPE_HEAP_OBJECT = 0x03,    PROFILER_PROPERTY_TYPE_EXTERNAL_OBJECT = 0x04,    PROFILER_PROPERTY_TYPE_BSTR = 0x05,} PROFILER_RELATIONSHIP_INFO;  
```  
  
## <a name="members"></a>Miembros  
  
|Miembro|Valor|Descripción|  
|------------|-----------|-----------------|  
|PROFILER_PROPERTY_TYPE_NUMBER|0x01|El objeto es un número.|  
|PROFILER_PROPERTY_TYPE_STRING|0x02|El objeto es una cadena.|  
|PROFILER_PROPERTY_TYPE_HEAP_OBJECT|0x03|El objeto es un objeto de montón.|  
|PROFILER_PROPERTY_TYPE_EXTERNAL_OBJECT|0x04|El objeto es externo, es decir, no en el montón de elementos no utilizados.|  
|PROFILER_PROPERTY_TYPE_BSTR|0x05|El objeto es una cadena BSTR.|  
|PROFILER_PROPERTY_TYPE_SUBSTRING|0x06|El objeto es una SUBCADENA.|