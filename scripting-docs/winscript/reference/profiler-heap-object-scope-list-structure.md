---
title: "PROFILER_HEAP_OBJECT_SCOPE_LIST (Estructura) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 33ebaa31-0a35-47d5-a4e3-afd83e16f53e
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# PROFILER_HEAP_OBJECT_SCOPE_LIST (Estructura)
Esta estructura se asocia los objetos de función únicamente.  La lista de ámbito representa el cierre de la función como lista de ámbitos donde es un objeto cada ámbito de pila con una lista de propiedades asociada que representa variables en cada ámbito determinado.  En algunos casos, los nombres de objetos en ese ámbito no estén disponibles, y únicamente su índice en la lista de propiedades está disponible.  
  
## Sintaxis  
  
```  
typedef struct _PROFILER_HEAP_OBJECT_SCOPE_LIST  
{  
    UINT count;  
    [size_is(count)] PROFILER_HEAP_OBJECT_ID scopes[];  
} PROFILER_HEAP_OBJECT_SCOPE_LIST;  
  
```  
  
## Members  
  
|Miembro|Tipo|Descripción|  
|-------------|----------|-----------------|  
|count|UINT|El número de ámbitos|  
|scopes|[PROFILER\_HEAP\_OBJECT\_ID \(Tipo\)](../../winscript/reference/profiler-heap-object-id-type.md)|Una matriz de ámbitos.|