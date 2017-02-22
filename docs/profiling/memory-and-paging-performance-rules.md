---
title: "Reglas de rendimiento de memoria y paginaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f37972b2-efe4-4a1c-a5d1-a246ccd76817
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Reglas de rendimiento de memoria y paginaci&#243;n
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Las reglas de rendimiento de la memoria y la categoría del archivo de paginación identifican la actividad del archivo de paginación en una ejecución de generación de perfiles que puede afectar al rendimiento y capacidad de respuesta de la aplicación.  
  
|||  
|-|-|  
|[DA0014: Frecuencia extremadamente alta de paginación de memoria activa en el disco](../Topic/DA0014:%20Extremely%20high%20rates%20of%20paging%20active%20memory%20to%20disk.md)|Una tasa sumamente alta de memoria activa para el archivo de paginación tuvo lugar durante la ejecución de generación de perfiles.  Las tasas de paginación en este nivel normalmente afectan al rendimiento de la aplicación y su capacidad de respuesta.  Puede reducir las asignaciones de memoria mediante la revisión de los algoritmos.  Quizás tenga que considerar también los requisitos de memoria de la aplicación  Intente generar los perfiles en un equipo con más memoria.  Esta regla se desencadena cuando la cantidad de la actividad de paginación supera el umbral máximo de la regla D0017.|  
|[DA0017: Tasas altas de memoria paginada activa en disco](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md)|Una tasa relativamente alta de memoria activa para paginación tuvo lugar en el disco durante la ejecución de generación de perfiles.  Las tasas de paginación en este nivel normalmente afectan al rendimiento de la aplicación y su capacidad de respuesta.  Puede reducir las asignaciones de memoria mediante la revisión de los algoritmos.  Quizás tenga que considerar también los requisitos de memoria de la aplicación  Intente generar los perfiles en un equipo con más memoria.|