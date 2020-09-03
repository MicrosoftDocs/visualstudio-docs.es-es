---
title: 'CA1600: no utilizar la prioridad del proceso inactiva | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotUseIdleProcessPriority
- CA1600
helpviewer_keywords:
- CA1600
- DoNotUseIdleProcessPriority
ms.assetid: 9b0d073b-78b6-41be-8ef3-14692a735283
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 3f6233136dcf7f1db5d622a02419d33e0eedacf5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545683"
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600: No utilizar la prioridad del proceso inactiva
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|DoNotUseIdleProcessPriority|
|Identificador de comprobación|CA1600|
|Category|Microsoft. Mobility|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
 Esta regla se produce cuando los procesos se establecen en `ProcessPriorityClass.Idle` .

## <a name="rule-description"></a>Descripción de la regla
 No establezca la prioridad de proceso en Idle. Los procesos que tienen `System.Diagnostics.ProcessPriorityClass.Idle` ocuparán la CPU cuando de otro modo estuvieran inactivos y, por tanto, se bloquearán en modo de espera.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Establezca procesos en `ProcessPriorityClass.BelowNormal` .

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Esta regla solo se debe suprimir cuando se requiere la prioridad del proceso inactivo y las consideraciones de movilidad se pueden omitir de forma segura.
