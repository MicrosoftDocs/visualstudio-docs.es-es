---
title: 'CA1601: No utilizar temporizadores que impidan los cambios de estado de energía | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
helpviewer_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
ms.assetid: b8028c92-0696-4c54-9773-0028f29bda9a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 270c030d4d4b829fb1e7d17308a4ae6f0ad17539
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="ca1601-do-not-use-timers-that-prevent-power-state-changes"></a>CA1601: No utilizar temporizadores que impidan los cambios de estado de energía
|||  
|-|-|  
|TypeName|DoNotUseTimersThatPreventPowerStateChanges|  
|Identificador de comprobación|CA1601|  
|Categoría|Microsoft.Mobility|  
|Cambio problemático|Problemático|  
  
## <a name="cause"></a>Motivo  
 Un temporizador tiene un intervalo establecido que se produzca más de una vez por segundo.  
  
## <a name="rule-description"></a>Descripción de la regla  
 No se debe sondear con más frecuencia que una vez por segundo o utilizar temporizadores que se producen con más frecuencia que una vez por segundo. Una actividad periódica más frecuente hará que la CPU no esté disponible, e interferirá con los temporizadores de inactividad para ahorro de energía, que apagan el monitor y el disco duro.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Establecer los intervalos de temporizador que se produzcan menos de una vez por segundo.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 Esta regla se debe suprimir únicamente si desencadenar el temporizador más de una vez por segundo es necesario y las consideraciones de movilidad pueden omitir.