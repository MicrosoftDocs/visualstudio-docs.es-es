---
title: 'CA2004: Quitar las llamadas a GC.KeepAlive'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
helpviewer_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
ms.assetid: bc543b5b-23eb-4b45-abc2-9325cd254ac2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0e025a8af3f7f5c1810abe2b9e182f607a29760e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53915842"
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
 Si va a convertir a `SafeHandle` uso, quite todas las llamadas a `GC.KeepAlive` (objeto). En este caso, las clases no debe llamar a `GC.KeepAlive`, suponiendo que no tienen un finalizador sino que se basan en `SafeHandle` para completar el identificador del sistema operativo para ellos.  Aunque el costo de dejar en una llamada a `GC.KeepAlive` puede ser insignificante con relación al rendimiento, la percepción de que una llamada a `GC.KeepAlive` es necesaria o suficiente para solucionar el problema que puedan existir ya no hace que el código sea más difícil de un período de duración mantener.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Quite las llamadas a `GC.KeepAlive`.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 Puede suprimir esta advertencia solo si no es técnicamente correcta convertir a `SafeHandle` uso en la clase.