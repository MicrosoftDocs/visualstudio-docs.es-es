---
title: Advertencias de movilidad | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.MobilityRules
helpviewer_keywords:
- managed code analysis warnings, mobility warnings
- mobility warnings
- warnings, mobility
ms.assetid: 9808054c-593b-4fc3-92cc-1fc45f41569c
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7fdcff36e689961200497298f3360fc0efb27f0a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="mobility-warnings"></a>advertencias de movilidad
Advertencias de movilidad son compatibles con uso eficiente de energía.  
  
## <a name="in-this-section"></a>En esta sección  
  
|Regla|Descripción|  
|----------|-----------------|  
|[CA1600: No utilizar la prioridad del proceso inactiva](../code-quality/ca1600-do-not-use-idle-process-priority.md)|No establezca la prioridad de proceso en Idle. Los procesos que tienen System.Diagnostics.ProcessPriorityClass.Idle ocupan la CPU cuando, de otro modo, estaría inactiva y, por consiguiente, bloquean el estado de espera.|  
|[CA1601: No utilizar temporizadores que impidan los cambios de estado de energía](../code-quality/ca1601-do-not-use-timers-that-prevent-power-state-changes.md)|Una actividad periódica más frecuente hará que la CPU no esté disponible, e interferirá con los temporizadores de inactividad para ahorro de energía, que apagan el monitor y el disco duro.|