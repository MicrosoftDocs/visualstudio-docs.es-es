---
title: 'CA1600: No utilizar la prioridad del proceso inactiva | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotUseIdleProcessPriority
- CA1600
helpviewer_keywords:
- CA1600
- DoNotUseIdleProcessPriority
ms.assetid: 9b0d073b-78b6-41be-8ef3-14692a735283
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 2d1646cd587295f2854399cfc24603ce1f1910e6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
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