---
title: "Active Script Profiler (Constantes, enumeraciones y estructuras) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 6e079d84-9dde-46fc-8a6a-18e902f60ecc
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Active Script Profiler (Constantes, enumeraciones y estructuras)
Active Script Profiler Interfaces utiliza las enumeraciones siguientes.  
  
## Constantes, enumeraciones y estructuras  
  
|Constantes|Descripción|  
|----------------|-----------------|  
|[PROFILER\_EXTERNAL\_OBJECT\_ADDRESS \(Tipo\)](../../winscript/reference/profiler-external-object-address-type.md)|Dirección del objeto externo del generador de perfiles.  Se utiliza en [PROFILER\_HEAP\_OBJECT \(Estructura\)](../../winscript/reference/profiler-heap-object-structure.md) y [PROFILER\_HEAP\_OBJECT\_RELATIONSHIP \(Estructura\)](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|[PROFILER\_HEAP\_OBJECT\_ID \(Tipo\)](../../winscript/reference/profiler-heap-object-id-type.md)|Identificador del objeto de montón.  Se utiliza en [PROFILER\_HEAP\_OBJECT \(Estructura\)](../../winscript/reference/profiler-heap-object-structure.md) [PROFILER\_HEAP\_OBJECT\_SCOPE\_LIST \(Estructura\)](../../winscript/reference/profiler-heap-object-scope-list-structure.md), [PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO \(Estructura\)](../../winscript/reference/profiler-heap-object-optional-info-structure.md) y [PROFILER\_HEAP\_OBJECT\_RELATIONSHIP \(Estructura\)](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|[PROFILER\_HEAP\_OBJECT\_NAME\_ID \(Tipo\)](../../winscript/reference/profiler-heap-object-name-id-type.md)|Identificador del nombre del objeto de montón.  Se utiliza en [PROFILER\_HEAP\_OBJECT \(Estructura\)](../../winscript/reference/profiler-heap-object-structure.md).|  
  
|Enumeraciones|Descripción|  
|-------------------|-----------------|  
|[PROFILER\_EVENT\_MASK \(Enumeración\)](../../winscript/reference/profiler-event-mask-enumeration.md)|Indica los tipos de eventos de los que se deben generar perfiles.|  
|[PROFILER\_HEAP\_ENUM\_FLAGS \(Enumeración\)](../../winscript/reference/profiler-heap-enum-flags-enumeration.md)|Marcas que representan si se expone información adicional sobre un objeto de montón al que se apunta en una relación de objeto.  Se utiliza en [IActiveScriptProfilerControl5::EnumHeap2 \(Método\)](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md).|  
|[PROFILER\_HEAP\_OBJECT\_FLAGS \(Enumeración\)](../../winscript/reference/profiler-heap-object-flags-enumeration.md)|Marcas que representan información básica sobre el objeto de montón.  Se utiliza en [PROFILER\_HEAP\_OBJECT \(Estructura\)](../../winscript/reference/profiler-heap-object-structure.md).|  
|[PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO\_TYPE \(Enumeración\)](../../winscript/reference/profiler-heap-object-optional-info-type-enumeration.md)|Representa distintos tipos de información opcional.  Se utiliza en [PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO \(Estructura\)](../../winscript/reference/profiler-heap-object-optional-info-structure.md).|  
|[PROFILER\_RELATIONSHIP\_INFO \(Enumeración\)](../../winscript/reference/profiler-relationship-info-enumeration.md)|Representa información sobre el objeto en la relación.  Se utiliza en [PROFILER\_HEAP\_OBJECT\_RELATIONSHIP \(Estructura\)](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|[PROFILER\_SCRIPT\_TYPE \(Enumeración\)](../../winscript/reference/profiler-script-type-enumeration.md)|Especifica el tipo de script.|  
  
|Estructuras|Descripción|  
|-----------------|-----------------|  
|[PROFILER\_HEAP\_OBJECT \(Estructura\)](../../winscript/reference/profiler-heap-object-structure.md)|Representa los objetos de montón recopilados por [IActiveScriptProfilerControl3::EnumHeap \(Método\)](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).|  
|[PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO \(Estructura\)](../../winscript/reference/profiler-heap-object-optional-info-structure.md)|Representa información opcional sobre objetos de montón.|  
|[PROFILER\_HEAP\_OBJECT\_RELATIONSHIP \(Estructura\)](../../winscript/reference/profiler-heap-object-relationship-structure.md)|Representa una relación de un objeto de montón.|  
|[PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_LIST \(Estructura\)](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Representa una lista de relaciones que pertenecen a un objeto de montón.|  
|[PROFILER\_HEAP\_OBJECT\_SCOPE\_LIST \(Estructura\)](../../winscript/reference/profiler-heap-object-scope-list-structure.md)|Esta estructura solo se asocia a objetos de función.  La lista de ámbitos representa el cierre de la función como una lista de ámbitos donde cada ámbito es un objeto de montón con una lista de propiedades asociada que representa variables en cada ámbito determinado.  En algunos casos, puede que los nombres de los objetos de ese ámbito no estén disponibles; solo están disponibles sus identificadores.|  
  
## Vea también  
 [Active Script Profiler \(Interfaces\)](../../winscript/reference/active-script-profiler-interfaces.md)