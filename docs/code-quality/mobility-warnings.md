---
title: advertencias de movilidad
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- vs.codeanalysis.MobilityRules
helpviewer_keywords:
- managed code analysis warnings, mobility warnings
- mobility warnings
- warnings, mobility
ms.assetid: 9808054c-593b-4fc3-92cc-1fc45f41569c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 47bb602da5483b3ea31513b6185ce00e07200a42
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54974011"
---
# <a name="mobility-warnings"></a>advertencias de movilidad
Advertencias de movilidad admiten el uso eficiente de energía.

## <a name="in-this-section"></a>En esta sección

|Regla|Descripción|
|----------|-----------------|
|[CA1600: No utilice la prioridad del proceso inactiva](../code-quality/ca1600-do-not-use-idle-process-priority.md)|No establezca la prioridad de proceso en Idle. Los procesos que tienen System.Diagnostics.ProcessPriorityClass.Idle ocupan la CPU cuando, de otro modo, estaría inactiva y, por consiguiente, bloquean el estado de espera.|
|[CA1601: No utilizar temporizadores que impidan los cambios de estado de energía](../code-quality/ca1601-do-not-use-timers-that-prevent-power-state-changes.md)|Una actividad periódica más frecuente hará que la CPU no esté disponible, e interferirá con los temporizadores de inactividad para ahorro de energía, que apagan el monitor y el disco duro.|