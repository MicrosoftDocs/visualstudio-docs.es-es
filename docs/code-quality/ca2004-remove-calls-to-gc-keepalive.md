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
ms.workload: multiple
ms.openlocfilehash: dd6cc8b51ddd8f9e8813229cf66b9facb52e4668
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
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