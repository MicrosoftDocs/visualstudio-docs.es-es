---
title: 'CA1304: Especificar CultureInfo'
ms.date: 06/30/2018
ms.topic: reference
f1_keywords:
- SpecifyCultureInfo
- CA1304
helpviewer_keywords:
- SpecifyCultureInfo
- CA1304
ms.assetid: b912d76a-54fd-4c93-b25d-16491e0ae319
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2539cef9e6b2fe20513943f686aeaa1ff7a79013
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235102"
---
# <a name="ca1304-specify-cultureinfo"></a>CA1304: Especificar CultureInfo

|||
|-|-|
|TypeName|SpecifyCultureInfo|
|Identificador de comprobación|CA1304|
|Categoría|Microsoft. Globalization|
|Cambio importante|Poco problemático|

## <a name="cause"></a>Motivo

Un método o constructor llama a un miembro que tiene una sobrecarga que acepta <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> un parámetro y el método o constructor no llama a la sobrecarga que toma el <xref:System.Globalization.CultureInfo> parámetro. Esta regla omite las llamadas a los métodos siguientes:

- <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>

## <a name="rule-description"></a>Descripción de la regla

Cuando no <xref:System.Globalization.CultureInfo> se <xref:System.IFormatProvider?displayProperty=nameWithType> proporciona un objeto o, es posible que el valor predeterminado proporcionado por el miembro sobrecargado no tenga el efecto deseado en todas las configuraciones regionales. Además, los miembros de .NET eligen la referencia cultural y el formato predeterminados en función de las suposiciones que podrían no ser correctas para el código. Para asegurarse de que el código funciona según lo previsto en los escenarios, debe proporcionar información específica de la referencia cultural según las siguientes directrices:

- Si el valor se va a mostrar al usuario, use la referencia cultural actual. Vea <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.

- Si el valor se almacenará y tendrá acceso a él mediante software, es decir, se conserva en un archivo o base de datos, use la referencia cultural de todos los idiomas. Vea <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.

- Si no conoce el destino del valor, haga que el consumidor de datos o el proveedor especifiquen la referencia cultural.

Incluso si el comportamiento predeterminado del miembro sobrecargado es adecuado para sus necesidades, es mejor llamar explícitamente a la sobrecarga específica de la referencia cultural para que el código se autodocumente y se mantenga más fácilmente.

> [!NOTE]
> <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType>solo se usa para recuperar recursos localizados mediante una instancia de la <xref:System.Resources.ResourceManager?displayProperty=nameWithType> clase.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, use la sobrecarga que toma <xref:System.Globalization.CultureInfo> un argumento.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

Es seguro suprimir una advertencia de esta regla cuando está seguro de que la referencia cultural predeterminada es la opción correcta y donde el mantenimiento del código no es una prioridad de desarrollo importante.

## <a name="example-showing-how-to-fix-violations"></a>Ejemplo que muestra cómo corregir infracciones

En el ejemplo siguiente, `BadMethod` se producen dos infracciones de esta regla. `GoodMethod`corrige la primera infracción pasando la referencia cultural de todos los <xref:System.String.Compare%2A?displayProperty=nameWithType>idiomas a y corrige la segunda infracción pasando la referencia cultural actual <xref:System.String.ToLower%2A?displayProperty=nameWithType> a `string3` porque se muestra al usuario.

[!code-csharp[FxCop.Globalization.CultureInfo#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_1.cs)]

## <a name="example-showing-formatted-output"></a>Ejemplo que muestra la salida con formato

En el ejemplo siguiente se muestra el efecto de la referencia cultural <xref:System.IFormatProvider> actual en el valor predeterminado <xref:System.DateTime> seleccionado por el tipo.

[!code-csharp[FxCop.Globalization.IFormatProvider#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_2.cs)]

Este ejemplo produce el siguiente resultado:

```txt
6/4/1900 12:15:12 PM
06/04/1900 12:15:12
```

## <a name="related-rules"></a>Reglas relacionadas

- [CA1305: Especificar IFormatProvider](../code-quality/ca1305-specify-iformatprovider.md)

## <a name="see-also"></a>Vea también

- [Usar la clase CultureInfo](/dotnet/standard/globalization-localization/globalization#work-with-culture-specific-settings)