---
title: 'CA2004: Quite las llamadas a GC. KeepAlive | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
helpviewer_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
ms.assetid: bc543b5b-23eb-4b45-abc2-9325cd254ac2
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e75ab22212945e5a6b4465e1e1f64ca48a9daa4a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68189046"
---
# <a name="ca2004-remove-calls-to-gckeepalive"></a>CA2004: Quitar las llamadas a GC.KeepAlive
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|RemoveCallsToGCKeepAlive|
|Identificador de comprobación|CA2004|
|Categoría|Microsoft.Reliability|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Causa
 Clases utilizan `SafeHandle` pero sigue sin contener las llamadas a `GC.KeepAlive`.

## <a name="rule-description"></a>Descripción de la regla
 Si va a convertir a `SafeHandle` uso, quite todas las llamadas a `GC.KeepAlive` (objeto). En este caso, las clases no debe llamar a `GC.KeepAlive`, suponiendo que no tienen un finalizador sino que se basan en `SafeHandle` para completar el identificador del sistema operativo para ellos.  Aunque el costo de dejar en una llamada a `GC.KeepAlive` puede ser insignificante con relación al rendimiento, la percepción de que una llamada a `GC.KeepAlive` es necesaria o suficiente para solucionar el problema que puedan existir ya no hace que el código sea más difícil de un período de duración mantener.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Quite las llamadas a `GC.KeepAlive`.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Puede suprimir esta advertencia solo si no es técnicamente correcta convertir a `SafeHandle` uso en la clase.
