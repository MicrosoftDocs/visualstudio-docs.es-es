---
title: "Vista Funciones: datos de muestreo de memoria de .NET del generador de perfiles | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Funciones (vista)"
ms.assetid: 5d9c6302-2ffd-430e-9535-13ce795f9f7c
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Vista Funciones: datos de muestreo de memoria de .NET del generador de perfiles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La vista Funciones de los datos de generación de perfiles de asignación de memoria de .NET recopilados mediante el método de muestreo enumera las funciones que asignaron memoria durante la ejecución de generación de perfiles e indica el tamaño y el número de asignaciones.  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Id. de proceso**|Identificador de proceso \(PID\) de la generación de perfiles.|  
|**Nombre del proceso**|Nombre del proceso.|  
|**Nombre de módulo**|Nombre del módulo que contiene la función.|  
|**Ruta de acceso del módulo**|Ruta de acceso del módulo que contiene la función.|  
|**Archivo de origen**|Archivo de origen que contiene la definición de esta función.|  
|**Nombre de la función**|El nombre completo de la función.|  
|**Número de línea de función**|Número de línea del inicio de esta función en el archivo de origen.|  
|**Dirección de función**|Dirección de la función.|  
|**Asignaciones de inclusión**|Número total de objetos asignados en esta función y en sus funciones secundarias.|  
|**Porcentaje de asignaciones inclusivas**|Porcentaje de todos los objetos asignados durante la generación de perfiles que fueron objeto de asignaciones inclusivas de esta función.|  
|**Asignaciones de exclusión**|El número de objetos creados cuando la función se estaba ejecutando directamente en la parte superior de la pila de llamadas.  Este número no incluye los objetos creados en las funciones secundarias.|  
|**Porcentaje de asignaciones exclusivas**|Porcentaje de todos los objetos asignados durante la generación de perfiles que fueron objeto de asignaciones exclusivas de esta función.|  
|**Bytes inclusivos**|Número de bytes de memoria asignados por esta función y por sus funciones secundarias.|  
|**Porcentaje de bytes inclusivos**|Porcentaje de todos los bytes de memoria asignados durante la generación de perfiles que fueron bytes inclusivos de esta función.|  
|**Bytes exclusivos**|Número de bytes de memoria asignados por esta función pero no por sus funciones secundarias.|  
|**Porcentaje de bytes exclusivos**|Porcentaje de todos los bytes de memoria asignados durante la generación de perfiles que fueron bytes exclusivos de esta función.|  
  
## Vea también  
 [Vista de funciones \- Instrumentación](../profiling/functions-view-dotnet-memory-instrumentation-data.md)   
 [Vista Funciones](../profiling/functions-view-sampling-data.md)   
 [Vista Funciones](../profiling/functions-view-instrumentation-data.md)