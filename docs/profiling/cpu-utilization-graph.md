---
title: "Gr&#225;fico de utilizaci&#243;n de la CPU | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.cpu.graph"
helpviewer_keywords: 
  - "Gráfico de utilización de la CPU, visualizador de simultaneidad, gráfico de utilización de la CPU"
ms.assetid: 5332fd38-622d-47a3-874f-8c2fd7a30f95
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Gr&#225;fico de utilizaci&#243;n de la CPU
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El gráfico de utilización de la CPU muestra el nivel de uso de una aplicación a lo largo del tiempo.  El eje X representa la duración de la aplicación y el eje Y, el número de núcleos lógicos del sistema.  El gráfico no muestra qué núcleo específico está activo en un momento determinado.  Por ejemplo, si dos núcleos se están ejecutando cada uno al 50 por ciento de su capacidad en un período de tiempo determinado, esta vista mostrará que se está utilizando un núcleo lógico.  
  
## Colores del gráfico de utilización de la CPU  
  
-   El verde indica la utilización de núcleos lógicos del sistema por el proceso actual.  
  
-   El gris claro indica la utilización de núcleos lógicos por otros procesos del sistema.  Un porcentaje alto de gris claro en el gráfico indica que otros procesos suponen una carga importante para el sistema y que tendrán preferencia sobre el suyo.  Para reducir el consumo de núcleos lógicos por parte de otros procesos, reduzca el número de procesos que se ejecutan el sistema.  
  
-   El gris oscuro indica el consumo de núcleos lógicos por parte del proceso del sistema.  No se puede controlar este hecho directamente, pero es útil conocer cuándo se está produciendo, porque puede afectar a la disponibilidad de núcleos lógicos para el proceso.  
  
-   El blanco indica la disponibilidad de núcleos lógicos no utilizados en el sistema.  Estos núcleos están disponibles para el proceso si puede encontrar más oportunidades para el paralelismo.  
  
## Vea también  
 [Vista de utilización](../profiling/utilization-view.md)   
 [Uso medio de la CPU](../profiling/average-cpu-utilization.md)