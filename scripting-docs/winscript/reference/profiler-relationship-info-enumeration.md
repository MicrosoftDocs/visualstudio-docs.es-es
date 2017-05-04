---
title: "PROFILER_RELATIONSHIP_INFO (Enumeraci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: fae69317-6224-4a6a-8e9e-ccaa6a330818
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# PROFILER_RELATIONSHIP_INFO (Enumeraci&#243;n)
Representa información sobre el objeto en la relación.  Se usa en [PROFILER\_HEAP\_OBJECT\_RELATIONSHIP \(Estructura\)](../../winscript/reference/profiler-heap-object-relationship-structure.md).  
  
## Sintaxis  
  
```  
typedef [v1_enum] enum {  
    PROFILER_PROPERTY_TYPE_NUMBER = 0x01,  
    PROFILER_PROPERTY_TYPE_STRING = 0x02,  
    PROFILER_PROPERTY_TYPE_HEAP_OBJECT = 0x03,  
    PROFILER_PROPERTY_TYPE_EXTERNAL_OBJECT = 0x04,  
    PROFILER_PROPERTY_TYPE_BSTR = 0x05,  
} PROFILER_RELATIONSHIP_INFO;  
  
```  
  
## Members  
  
|Miembro|Valor|Descripción|  
|-------------|-----------|-----------------|  
|PROFILER\_PROPERTY\_TYPE\_NUMBER|0x01|El objeto es un número.|  
|PROFILER\_PROPERTY\_TYPE\_STRING|0x02|El objeto es una cadena.|  
|PROFILER\_PROPERTY\_TYPE\_HEAP\_OBJECT|0x03|El objeto es un objeto de la pila.|  
|PROFILER\_PROPERTY\_TYPE\_EXTERNAL\_OBJECT|0x04|El objeto es externo, es decir, no en la pila de la recolección de elementos no utilizados.|  
|PROFILER\_PROPERTY\_TYPE\_BSTR|0x05|El objeto es un valor BSTR.|