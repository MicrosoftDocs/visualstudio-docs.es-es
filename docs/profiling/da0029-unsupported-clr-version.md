---
title: "DA0029: Versi&#243;n de CLR incompatible | Microsoft Docs"
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
  - "vs.performance.29"
  - "vs.performance.rules.DA0029"
helpviewer_keywords: 
  - "vs.performance.29"
  - "vs.performance.rules.DA0029"
  - "vs.performance.rules.DA0029"
ms.assetid: 76247259-c6f3-44c4-b3f9-d8dac16b5e0d
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0029: Versi&#243;n de CLR incompatible
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|Identificador de regla|DA0029|  
|Categoría|Uso de Herramientas de generación de perfiles|  
|Método de generación de perfiles|Generación de perfiles desde la línea de comandos|  
|Mensaje|Se detectó una versión de CLR no admitida durante la recolección.  Los símbolos administrados pueden no resolverse correctamente.|  
|Tipo de regla|Información|  
  
## Motivo  
 Está intentando generar perfiles de una aplicación que utiliza [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)], que no es compatible con las Herramientas de generación de perfiles.  
  
## Descripción de la regla  
 Esta advertencia se produce porque las Herramientas de generación de perfiles no podrán solucionar los símbolos del código administrado que se ejecuta en la aplicación.  Las Herramientas de generación de perfiles no pueden solucionar los símbolos del código administrado de las aplicaciones que están ejecutando [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)].  
  
## Cómo corregir infracciones  
 Ninguno.