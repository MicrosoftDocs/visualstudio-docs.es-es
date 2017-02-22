---
title: "Gr&#225;fico de actividad de GPU | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.cpu.graph.gpu"
ms.assetid: d7c769af-95fb-49a3-b5ab-deafecee46fa
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gr&#225;fico de actividad de GPU
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El diagrama de actividad de GPU en el visualizador de simultaneidad muestra el nivel de actividad de DirectX en el sistema según lo medido por el número de motores de DirectX que están en uso con el tiempo.  El gráfico no muestra qué motores específicos fueron utilizados.  Un motor se considera en uso si está procesando cualquier trabajo de GPU.  
  
## Colores del gráfico de actividad de GPU  
 El verde indica el consumo de motores de DirectX por el proceso actual.  
  
 El gris claro indica el consumo de motores de DirectX por otros procesos del sistema.  Para reducir el consumo de motores de DirectX por parte de otros procesos, reduzca el número de procesos que se ejecutan en el sistema.  
  
 El blanco indica la disponibilidad de motores de DirectX no usados en el sistema.  Estos motores están disponibles para el proceso si puede encontrar más oportunidades para aprovecharlos.  Algunos motores sólo se pueden usar para determinados tipos de tareas.  
  
## Vea también  
 [Vista de utilización](../profiling/utilization-view.md)