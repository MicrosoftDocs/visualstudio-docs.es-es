---
title: Mobility Warnings
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.MobilityRules
helpviewer_keywords:
- managed code analysis warnings, mobility warnings
- mobility warnings
- warnings, mobility
ms.assetid: 9808054c-593b-4fc3-92cc-1fc45f41569c
author: jillre
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a58bd6232d25d3151b019fc774befc99d9e46e6b
ms.sourcegitcommit: 00ba14d9c20224319a5e93dfc1e0d48d643a5fcd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2020
ms.locfileid: "77091748"
---
# <a name="mobility-warnings"></a>Mobility Warnings
Las advertencias de movilidad admiten un uso eficaz de energía.

## <a name="in-this-section"></a>En esta sección

|Regla|Descripción|
|----------|-----------------|
|[CA1600: No utilizar la prioridad del proceso inactiva](../code-quality/ca1600.md)|No establezca la prioridad de proceso en Idle. Los procesos que tienen System.Diagnostics.ProcessPriorityClass.Idle ocupan la CPU cuando, de otro modo, estaría inactiva y, por consiguiente, bloquean el estado de espera.|
|[CA1601: No utilizar temporizadores que impidan los cambios de estado de energía](../code-quality/ca1601.md)|Una actividad periódica más frecuente hará que la CPU no esté disponible, e interferirá con los temporizadores de inactividad para ahorro de energía, que apagan el monitor y el disco duro.|
