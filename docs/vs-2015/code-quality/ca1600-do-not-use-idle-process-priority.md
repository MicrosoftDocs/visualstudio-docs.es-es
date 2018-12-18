---
title: 'CA1600: No utilizar la prioridad del proceso inactiva | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DoNotUseIdleProcessPriority
- CA1600
helpviewer_keywords:
- CA1600
- DoNotUseIdleProcessPriority
ms.assetid: 9b0d073b-78b6-41be-8ef3-14692a735283
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f077774f67ca398d26746d0c375545e0cb641454
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49941859"
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600: No utilizar la prioridad del proceso inactiva
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotUseIdleProcessPriority|
|Identificador de comprobación|CA1600|
|Categoría|Microsoft.Mobility|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Esta regla se produce cuando se establecen los procesos en `ProcessPriorityClass.Idle`.

## <a name="rule-description"></a>Descripción de la regla
 No establezca la prioridad de proceso en Idle. Los procesos que tienen `System.Diagnostics.ProcessPriorityClass.Idle` ocupan la CPU cuando estaría inactiva y, por lo tanto, se bloqueará en espera.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Establezca los procesos en `ProcessPriorityClass.BelowNormal`.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Esta regla se debe suprimir solo cuando se requiere la prioridad del proceso inactiva y las consideraciones de movilidad pueden hacer caso omiso sin ningún riesgo.



