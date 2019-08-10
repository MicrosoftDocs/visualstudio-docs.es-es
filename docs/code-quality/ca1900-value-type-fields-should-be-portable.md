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
ms.openlocfilehash: f734d0cf28a5aec28ebbf635dd384efe176b1774
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921321"
---
# <a name="ca1900-value-type-fields-should-be-portable"></a>CA1900: Los campos de tipo de valor deben ser portátiles

|||
|-|-|
|TypeName|ValueTypeFieldsShouldBePortable|
|Identificador de comprobación|CA1900|
|Categoría|Microsoft. portabilidad|
|Cambio problemático|Interrumpir: Si el campo puede verse fuera del ensamblado.<br /><br /> No problemático: Si el campo no es visible fuera del ensamblado.|

## <a name="cause"></a>Causa
Esta regla comprueba que las estructuras que se declaran con diseño explícito se alinearán correctamente cuando se calculen las referencias a código no administrado en sistemas operativos de 64 bits. IA-64 no permite el acceso a memoria no alineada y el proceso se bloqueará si esta infracción no es fija.

## <a name="rule-description"></a>Descripción de la regla
Las estructuras que tienen un diseño explícito que contiene campos desalineados causan bloqueos en los sistemas operativos de 64 bits.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Todos los campos de menos de 8 bytes deben tener desplazamientos que sean un múltiplo de su tamaño, y los campos de 8 bytes o más deben tener desplazamientos que sean un múltiplo de 8. Otra solución consiste en usar `LayoutKind.Sequential` en lugar de `LayoutKind.Explicit`, si es razonable.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
Esta advertencia solo se debe suprimir si se produce un error.