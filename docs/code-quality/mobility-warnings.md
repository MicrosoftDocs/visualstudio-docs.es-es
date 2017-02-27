---
title: "Advertencias de movilidad | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.MobilityRules"
helpviewer_keywords: 
  - "advertencias de análisis de código administrado, advertencias de movilidad"
  - "advertencias de movilidad"
  - "advertencias, movilidad"
ms.assetid: 9808054c-593b-4fc3-92cc-1fc45f41569c
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# Advertencias de movilidad
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Las advertencias de movilidad respaldan el uso eficaz de la energía.  
  
## En esta sección  
  
|Regla|Descripción|  
|-----------|-----------------|  
|[CA1600: No utilizar la prioridad del proceso inactiva](../code-quality/ca1600-do-not-use-idle-process-priority.md)|No establezca la prioridad de proceso en Idle.  Los procesos que tienen System.Diagnostics.ProcessPriorityClass.Idle ocupan la CPU cuando, de otro modo, estaría inactiva y, por consiguiente, bloquean el estado de espera.|  
|[CA1601: No utilizar temporizadores que impidan los cambios de estado de energía](../code-quality/ca1601-do-not-use-timers-that-prevent-power-state-changes.md)|Una actividad periódica más frecuente hará que la CPU no esté disponible e interferirá con los temporizadores de inactividad para ahorro de energía que apagan el monitor y el disco duro.|