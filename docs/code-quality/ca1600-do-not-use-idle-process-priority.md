---
title: 'CA1600: No utilizar la prioridad del proceso inactiva'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotUseIdleProcessPriority
- CA1600
helpviewer_keywords:
- CA1600
- DoNotUseIdleProcessPriority
ms.assetid: 9b0d073b-78b6-41be-8ef3-14692a735283
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c37affc585653807912d00c1cfe365853fd6260b
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921810"
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600: No utilizar la prioridad del proceso inactiva

|||
|-|-|
|TypeName|DoNotUseIdleProcessPriority|
|Identificador de comprobación|CA1600|
|Categoría|Microsoft.Mobility|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
Esta regla se produce cuando los procesos se `ProcessPriorityClass.Idle`establecen en.

## <a name="rule-description"></a>Descripción de la regla
No establezca la prioridad de proceso en Idle. Los procesos que `System.Diagnostics.ProcessPriorityClass.Idle` tienen ocuparán la CPU cuando de otro modo estuvieran inactivos y, por tanto, se bloquearán en modo de espera.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Establezca procesos en `ProcessPriorityClass.BelowNormal`.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
Esta regla solo se debe suprimir cuando se requiere la prioridad del proceso inactivo y las consideraciones de movilidad se pueden omitir de forma segura.