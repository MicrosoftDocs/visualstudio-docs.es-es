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
ms.openlocfilehash: 4bef51c547d4a1614137e0691343bef635aed50d
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233288"
---
# <a name="ca1900-value-type-fields-should-be-portable"></a>CA1900: Los campos de tipo de valor deben ser portátiles

|||
|-|-|
|TypeName|ValueTypeFieldsShouldBePortable|
|Identificador de comprobación|CA1900|
|Categoría|Microsoft. portabilidad|
|Cambio importante|Interrumpir: Si el campo puede verse fuera del ensamblado.<br /><br /> No problemático: Si el campo no es visible fuera del ensamblado.|

## <a name="cause"></a>Motivo
Esta regla comprueba que las estructuras que se declaran con diseño explícito se alinearán correctamente cuando se calculen las referencias a código no administrado en sistemas operativos de 64 bits. IA-64 no permite el acceso a memoria no alineada y el proceso se bloqueará si esta infracción no es fija.

## <a name="rule-description"></a>Descripción de la regla
Las estructuras que tienen un diseño explícito que contiene campos desalineados causan bloqueos en los sistemas operativos de 64 bits.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Todos los campos de menos de 8 bytes deben tener desplazamientos que sean un múltiplo de su tamaño, y los campos de 8 bytes o más deben tener desplazamientos que sean un múltiplo de 8. Otra solución consiste en usar `LayoutKind.Sequential` en lugar de `LayoutKind.Explicit`, si es razonable.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
Esta advertencia solo se debe suprimir si se produce un error.