---
title: 'CA1900: Los campos de tipo de valor deben ser portátiles'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1900
- ValueTypeFieldsShouldBePortable
helpviewer_keywords:
- ValueTypeFieldsShouldBePortable
- CA1900
ms.assetid: 1787d371-389f-4d39-b305-12b53bc0dfb9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e823a58d7a2be45c43305320bd32175de7a3fad6
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55953729"
---
# <a name="ca1900-value-type-fields-should-be-portable"></a>CA1900: Los campos de tipo de valor deben ser portátiles

|||
|-|-|
|TypeName|ValueTypeFieldsShouldBePortable|
|Identificador de comprobación|CA1900|
|Categoría|Microsoft.Portability|
|Cambio problemático|Importante: si el campo puede verse fuera del ensamblado.<br /><br /> No-importante: si el campo no está visible fuera del ensamblado.|

## <a name="cause"></a>Motivo
 Esta regla comprueba que las estructuras declaradas con un diseño explícito se alinearán correctamente cuando se calculan las referencias a código no administrado en sistemas operativos de 64 bits. IA-64 no permitir accesos memoria no alineada y el proceso se bloqueará si no se soluciona esta infracción.

## <a name="rule-description"></a>Descripción de la regla
 Estructuras que tienen un diseño explícito que contiene campos desalineados provocan bloqueos en sistemas operativos de 64 bits.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Deben tener todos los campos que tengan menos de 8 bytes desplazamientos que son un múltiplo de su tamaño y los campos que son 8 bytes o más deben tener los desplazamientos que son un múltiplo de 8. Otra solución consiste en usar `LayoutKind.Sequential` en lugar de `LayoutKind.Explicit`, si es razonable.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 Esta advertencia se debe suprimir solo si se produce en error.