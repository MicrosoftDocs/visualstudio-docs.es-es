---
title: 'CA2004: Quitar las llamadas a GC.KeepAlive'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a716da8eb0fb1b741c302ed32408e63a4933567b
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921133"
---
# <a name="ca2004-remove-calls-to-gckeepalive"></a>CA2004: Quitar las llamadas a GC.KeepAlive

|||
|-|-|
|TypeName|RemoveCallsToGCKeepAlive|
|Identificador de comprobación|CA2004|
|Categoría|Microsoft.Reliability|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Causa
Las clases `SafeHandle` usan pero todavía contienen llamadas `GC.KeepAlive`a.

## <a name="rule-description"></a>Descripción de la regla
Si está convirtiendo a `SafeHandle` uso, quite todas las llamadas `GC.KeepAlive` a (Object). En este caso, las clases no deben llamar `GC.KeepAlive`a, suponiendo que no tienen un finalizador sino que se basan en `SafeHandle` para completar el identificador del sistema operativo.  Aunque el costo de dejar en una llamada a `GC.KeepAlive` puede ser insignificante según lo medido por el rendimiento, la percepción de `GC.KeepAlive` que una llamada a es necesaria o suficiente para solucionar un problema de duración que puede que ya no exista hace que el código sea más difícil de manteni.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Quite las llamadas `GC.KeepAlive`a.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
Puede suprimir esta advertencia solo si no es técnicamente correcta para realizar la conversión `SafeHandle` al uso en la clase.