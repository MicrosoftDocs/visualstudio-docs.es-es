---
title: "Reglas de rendimiento de la supervisi&#243;n de recursos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f0f77faf-0a05-4718-a2c5-47934be40868
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Reglas de rendimiento de la supervisi&#243;n de recursos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Los mensajes de rendimiento en la categoría Supervisión de recursos proporcionan datos adicionales sobre el rendimiento de la aplicación.  Puede utilizarlos para analizar las degradaciones de rendimiento.  Estas reglas son informativas y se generan por cada ejecución de generación de perfiles.  
  
|||  
|-|-|  
|[DA0501: Promedio de consumo de CPU por parte del proceso que se va a perfilar.](../Topic/DA0501:%20Average%20CPU%20consumption%20by%20the%20Process%20being%20profiled..md)|Este mensaje indica el porcentaje de tiempo que un procesador estuvo ocupado ejecutando instrucciones de la aplicación.  El valor indicado es el promedio de todos los intervalos de medida en los que estaba activo el proceso para el que se generan perfiles.|  
|[DA0502: Máximo consumo de CPU por parte del proceso que se va a perfilar](../profiling/da0502-maximum-cpu-consumption-by-the-process-being-profiled.md)|Este mensaje indica el porcentaje de tiempo máximo que un procesador estuvo ocupado ejecutando instrucciones de la aplicación.  El valor indicado es el valor máximo indicado de todos los intervalos de medida en los que estaba activo el proceso para el que se generan perfiles.|  
|[DA0503: Promedio de conjuntos de trabajo en bytes para el proceso que se va a perfilar](../profiling/da0503-average-working-set-in-bytes-for-the-process-being-profiled.md)|Este mensaje indica la cantidad media de memoria física, en bytes, que el proceso estaba utilizando cuando la generación de perfiles estaba activa.  Esta medida de memoria física de conoce como espacio de trabajo.|  
|[DA0504: Conjunto de trabajo máximo en bytes para el proceso que se va a perfilar](../profiling/da0504-maximum-working-set-in-bytes-for-the-process-being-profiled.md)|Este mensaje indica la cantidad máxima de memoria física, en bytes, que el proceso estaba utilizando cuando la generación de perfiles estaba activa.|  
|[DA0505: Promedio de bytes privados asignados al proceso que se va a perfilar](../profiling/da0505-average-private-bytes-allocated-for-the-process-being-profiled.md)|Este mensaje indica la cantidad media de memoria virtual, en bytes, que el proceso había asignado cuando la generación de perfiles estaba activa.  Esta medida de memoria virtual se conoce como *bytes privados*.  Los bytes privados representan las ubicaciones de memoria virtual asignadas por el proceso a las que solo pueden tener acceso los subprocesos que se ejecutan dentro del proceso.|  
|[DA0506: Máximo de bytes privados asignados al proceso que se va a perfilar](../profiling/da0506-maximum-private-bytes-allocated-for-the-process-being-profiled.md)|Este mensaje indica la cantidad máxima de memoria virtual, en bytes privados, que el proceso había asignado cuando la generación de perfiles estaba activa.|