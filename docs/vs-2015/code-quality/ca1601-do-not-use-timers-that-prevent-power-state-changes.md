---
title: 'CA1601: no usar temporizadores que impidan cambios de estado de energía | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
helpviewer_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
ms.assetid: b8028c92-0696-4c54-9773-0028f29bda9a
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7928b2fff8c12ca3f0cc3c58bee31fe5809517e5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545644"
---
# <a name="ca1601-do-not-use-timers-that-prevent-power-state-changes"></a>CA1601: No utilizar temporizadores que impidan los cambios de estado de energía
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|DoNotUseTimersThatPreventPowerStateChanges|
|Identificador de comprobación|CA1601|
|Category|Microsoft. Mobility|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
 Un temporizador tiene un intervalo establecido para que tenga lugar más de una vez por segundo.

## <a name="rule-description"></a>Descripción de la regla
 No sondear más de una vez por segundo o usar temporizadores que se producen con más frecuencia que una vez por segundo. Una actividad periódica más frecuente hará que la CPU no esté disponible, e interferirá con los temporizadores de inactividad para ahorro de energía, que apagan el monitor y el disco duro.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Establezca intervalos de temporizador para que se produzcan menos de una vez por segundo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Esta regla solo se debe suprimir si se requiere la activación del temporizador más de una vez por segundo y las consideraciones de movilidad se pueden omitir sin ningún riesgo.
