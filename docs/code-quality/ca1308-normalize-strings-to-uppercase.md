---
title: 'CA1308: Normalizar cadenas en mayúsculas'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1308
- NormalizeStringsToUppercase
helpviewer_keywords:
- NormalizeStringsToUppercase
- CA1308
ms.assetid: 7e9a7457-3f93-4938-ac6f-1389fba8d9cc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c33f4b0b55728d659c34e0ffc8723f555a6d074d
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234925"
---
# <a name="ca1308-normalize-strings-to-uppercase"></a>CA1308: Normalizar cadenas en mayúsculas

|||
|-|-|
|TypeName|NormalizeStringsToUppercase|
|Identificador de comprobación|CA1308|
|Categoría|Microsoft. Globalization|
|Cambio importante|Poco problemático|

## <a name="cause"></a>Motivo
Una operación normaliza una cadena a minúsculas.

## <a name="rule-description"></a>Descripción de la regla
Las cadenas se deberían normalizar para que se escriban en letras mayúsculas. Un pequeño grupo de caracteres, cuando se convierten a minúsculas, no puede realizar un viaje de ida y vuelta. Realizar un viaje de ida y vuelta significa convertir los caracteres de una configuración regional a otra configuración regional que represente los datos de caracteres de forma diferente y, a continuación, recuperar con precisión los caracteres originales de los caracteres convertidos.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Cambie las operaciones que convierten cadenas en minúsculas para que las cadenas se conviertan a mayúsculas en su lugar. Por ejemplo, cambie `String.ToLower(CultureInfo.InvariantCulture)` a `String.ToUpper(CultureInfo.InvariantCulture)`.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
Es seguro suprimir un mensaje de advertencia cuando no se toma la decisión de seguridad basada en el resultado (por ejemplo, cuando se muestra en la interfaz de usuario).

## <a name="see-also"></a>Vea también
[Advertencias de globalización](../code-quality/globalization-warnings.md)