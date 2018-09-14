---
title: 'CA1308: Normalizar las cadenas en mayúsculas'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 358910be4245c5c00541a7a4f686226b6250e902
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/13/2018
ms.locfileid: "45545705"
---
# <a name="ca1308-normalize-strings-to-uppercase"></a>CA1308: Normalizar las cadenas en mayúsculas
|||
|-|-|
|TypeName|NormalizeStringsToUppercase|
|Identificador de comprobación|CA1308|
|Categoría|Microsoft.Globalization|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Una operación normaliza una cadena a minúsculas.

## <a name="rule-description"></a>Descripción de la regla
 Las cadenas se deberían normalizar para que se escriban en letras mayúsculas. Un pequeño grupo de caracteres al que se convierten a minúsculas, no se puede realizar un recorrido de ida y. Para realizar un recorrido de ida y medios para convertir los caracteres de una configuración regional para otra configuración regional que representa datos de caracteres de forma diferente y, a continuación, con precisión recuperan los caracteres originales de los caracteres convertidos.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Cambiar las operaciones que convierten cadenas a minúscula para que las cadenas se convierten a mayúsculas en su lugar. Por ejemplo, cambie `String.ToLower(CultureInfo.InvariantCulture)` a `String.ToUpper(CultureInfo.InvariantCulture)`.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 Es seguro suprimir un mensaje de advertencia cuando no estás realizando la decisión de seguridad en función del resultado (por ejemplo, cuando se muestran en la interfaz de usuario).

## <a name="see-also"></a>Vea también
 [Advertencias de globalización](../code-quality/globalization-warnings.md)