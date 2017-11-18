---
title: 'CA2004: Quitar las llamadas a GC. KeepAlive | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
helpviewer_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
ms.assetid: bc543b5b-23eb-4b45-abc2-9325cd254ac2
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: edb47391872da6754e39a27d2e8a50dc61293af1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="ca2004-remove-calls-to-gckeepalive"></a>CA2004: Quitar las llamadas a GC.KeepAlive
|||  
|-|-|  
|TypeName|RemoveCallsToGCKeepAlive|  
|Identificador de comprobación|CA2004|  
|Categoría|Microsoft.Reliability|  
|Cambio problemático|Poco problemático|  
  
## <a name="cause"></a>Motivo  
 Clases utilizan `SafeHandle` pero sigue sin contener las llamadas a `GC.KeepAlive`.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Si va a convertir a `SafeHandle` uso, quite todas las llamadas a `GC.KeepAlive` (objeto). En este caso, las clases no es necesario llamar a `GC.KeepAlive`, suponiendo que no tienen un finalizador sino que se basan en `SafeHandle` para completar el identificador de sistema operativo para ellos.  Aunque el costo de dejar en una llamada a `GC.KeepAlive` podría ser insignificante según la medición del rendimiento, la percepción de que una llamada a `GC.KeepAlive` es necesaria o suficiente para solucionar el problema que podría existir ya no hace que el código sea más difícil para un período de duración mantener.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Quite las llamadas a `GC.KeepAlive`.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 Puede suprimir esta advertencia sólo si no es técnicamente correcto realizar la conversión a `SafeHandle` uso de la clase.