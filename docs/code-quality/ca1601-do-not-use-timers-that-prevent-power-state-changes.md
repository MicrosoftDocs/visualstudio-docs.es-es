---
title: 'CA1601: No utilizar temporizadores que impidan los cambios de estado de energía'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
helpviewer_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
ms.assetid: b8028c92-0696-4c54-9773-0028f29bda9a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1300b733cbd4808359089787ceebeb0750de6723
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234342"
---
# <a name="ca1601-do-not-use-timers-that-prevent-power-state-changes"></a>CA1601: No utilizar temporizadores que impidan los cambios de estado de energía

|||
|-|-|
|TypeName|DoNotUseTimersThatPreventPowerStateChanges|
|Identificador de comprobación|CA1601|
|Categoría|Microsoft.Mobility|
|Cambio importante|Problemático|

## <a name="cause"></a>Motivo
Un temporizador tiene un intervalo establecido para que tenga lugar más de una vez por segundo.

## <a name="rule-description"></a>Descripción de la regla
No sondear más de una vez por segundo o usar temporizadores que se producen con más frecuencia que una vez por segundo. Una actividad periódica más frecuente hará que la CPU no esté disponible, e interferirá con los temporizadores de inactividad para ahorro de energía, que apagan el monitor y el disco duro.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Establezca intervalos de temporizador para que se produzcan menos de una vez por segundo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
Esta regla solo se debe suprimir si se requiere la activación del temporizador más de una vez por segundo y las consideraciones de movilidad se pueden omitir sin ningún riesgo.