---
title: 'CA1600: No utilizar la prioridad del proceso inactiva | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- DoNotUseIdleProcessPriority
- CA1600
helpviewer_keywords:
- CA1600
- DoNotUseIdleProcessPriority
ms.assetid: 9b0d073b-78b6-41be-8ef3-14692a735283
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 93255488efa84f553d61aaedb0474c69a4bbb8d0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600: No utilizar la prioridad del proceso inactiva
|||  
|-|-|  
|TypeName|DoNotUseIdleProcessPriority|  
|Identificador de comprobación|CA1600|  
|Categoría|Microsoft.Mobility|  
|Cambio problemático|Problemático|  
  
## <a name="cause"></a>Motivo  
 Esta regla se produce cuando se establecen procesos en `ProcessPriorityClass.Idle`.  
  
## <a name="rule-description"></a>Descripción de la regla  
 No establezca la prioridad de proceso en Idle. Los procesos que tienen `System.Diagnostics.ProcessPriorityClass.Idle` ocupan la CPU cuando en caso contrario, estaría inactiva y, por lo tanto, se bloqueará en espera.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Establezca los procesos en `ProcessPriorityClass.BelowNormal`.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 Esta regla se debe suprimir sólo cuando es necesaria la prioridad del proceso inactiva y las consideraciones de movilidad pueden hacer caso omiso sin ningún riesgo.