---
title: "CA1600: No utilizar la prioridad del proceso inactiva | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotUseIdleProcessPriority"
  - "CA1600"
helpviewer_keywords: 
  - "CA1600"
  - "DoNotUseIdleProcessPriority"
ms.assetid: 9b0d073b-78b6-41be-8ef3-14692a735283
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1600: No utilizar la prioridad del proceso inactiva
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotUseIdleProcessPriority|  
|Identificador de comprobación|CA1600|  
|Categoría|Microsoft.Mobility|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Esta regla se produce cuando los procesos se establecen en `ProcessPriorityClass.Idle`.  
  
## Descripción de la regla  
 No establezca la prioridad de proceso en Idle.  Los procesos que tienen `System.Diagnostics.ProcessPriorityClass.Idle` ocuparán la CPU cuando de lo contrario estaría inactiva y, por consiguiente, bloquearán la espera.  
  
## Cómo corregir infracciones  
 Establezca los procesos en `ProcessPriorityClass.BelowNormal`.  
  
## Cuándo suprimir advertencias  
 Esta regla solo se debe suprimir cuando se requiera la prioridad Idle para el proceso y se puedan pasar por alto las consideraciones de movilidad sin ningún riesgo.