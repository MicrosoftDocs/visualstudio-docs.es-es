---
title: "CA1601: No utilizar temporizadores que impidan los cambios de estado de energ&#237;a | Microsoft Docs"
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
  - "CA1601"
  - "DoNotUseTimersThatPreventPowerStateChanges"
helpviewer_keywords: 
  - "CA1601"
  - "DoNotUseTimersThatPreventPowerStateChanges"
ms.assetid: b8028c92-0696-4c54-9773-0028f29bda9a
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1601: No utilizar temporizadores que impidan los cambios de estado de energ&#237;a
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotUseTimersThatPreventPowerStateChanges|  
|Identificador de comprobación|CA1601|  
|Categoría|Microsoft.Mobility|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un temporizador tiene un intervalo establecido para producirse más de una vez por segundo.  
  
## Descripción de la regla  
 No se debe sondear más de una vez por segundo, ni se deben utilizar temporizadores que se produzcan más de una vez por segundo.  Una actividad periódica más frecuente hará que la CPU no esté disponible e interferirá con los temporizadores de inactividad para ahorro de energía que apagan el monitor y el disco duro.  
  
## Cómo corregir infracciones  
 Establezca los intervalos del temporizador de modo que ocurran menos de una vez por segundo.  
  
## Cuándo suprimir advertencias  
 Se debe suprimir esta regla solo si se debe desencadenar el temporizador varias veces por segundo y se pueden omitir las consideraciones de movilidad sin ningún riesgo.