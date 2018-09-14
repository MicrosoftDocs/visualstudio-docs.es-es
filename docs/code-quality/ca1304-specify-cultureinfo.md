---
title: 'CA1304: Especificar CultureInfo'
ms.date: 06/30/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fe02dd66b523e6ee82c5e1a2051f3a68839957d4
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/13/2018
ms.locfileid: "45546201"
---
# <a name="ca1304-specify-cultureinfo"></a>CA1304: Especificar CultureInfo

|||
|-|-|
|TypeName|SpecifyCultureInfo|
|Identificador de comprobación|CA1304|
|Categoría|Microsoft.Globalization|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo

Un método o constructor llama a un miembro que tiene una sobrecarga que acepta un <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> parámetro y el método o constructor no llama a la sobrecarga que toma el <xref:System.Globalization.CultureInfo> parámetro. Esta regla omite las llamadas a los métodos siguientes:

- <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>

## <a name="rule-description"></a>Descripción de la regla

Cuando un <xref:System.Globalization.CultureInfo> o <xref:System.IFormatProvider?displayProperty=nameWithType> objeto no se proporciona, el valor predeterminado proporcionado por el miembro sobrecargado podría no tener el efecto deseado en todas las configuraciones regionales. Además, los miembros de .NET Framework eligen la referencia cultural predeterminada y formato basado en suposiciones que pueden no ser correctas para su código. Para asegurarse de que el código funciona según lo esperado para sus escenarios, debería proporcionar información de referencia cultural específica según las siguientes directrices:

- Si el valor se mostrará al usuario, use la referencia cultural actual. Vea <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.

- Si el valor se almacenará y acceso a software, es decir, almacenado en un archivo o base de datos, use la referencia cultural invariable. Vea <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.

- Si no conoce el destino del valor, tiene el consumidor de datos o proveedor de especificar la referencia cultural.

Aunque el comportamiento predeterminado del miembro sobrecargado es adecuado para sus necesidades, es mejor llamar explícitamente a la sobrecarga de la referencia cultural específica para que el código sea más fácil de mantener y documenten por sí mismos.

> [!NOTE]
> <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> solo se utiliza para recuperar recursos localizados mediante el uso de una instancia de la <xref:System.Resources.ResourceManager?displayProperty=nameWithType> clase.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, use la sobrecarga que toma un <xref:System.Globalization.CultureInfo> argumento.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

Es seguro suprimir una advertencia de esta regla cuando se tiene la certeza de que la referencia cultural predeterminada es la elección correcta y mantención de código no es una prioridad de desarrollo importante.

## <a name="example-showing-how-to-fix-violations"></a>Ejemplo que muestra cómo corregir infracciones

En el ejemplo siguiente, `BadMethod` hace que dos infracciones de esta regla. `GoodMethod` corrige la primera infracción pasando la referencia cultural a <xref:System.String.Compare%2A?displayProperty=nameWithType>y corrige la segunda infracción pasando la referencia cultural actual a <xref:System.String.ToLower%2A?displayProperty=nameWithType> porque `string3` se muestra al usuario.

[!code-csharp[FxCop.Globalization.CultureInfo#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_1.cs)]

## <a name="example-showing-formatted-output"></a>Salida con formato que muestra de ejemplo

El ejemplo siguiente muestra el efecto de la referencia cultural actual en el valor predeterminado <xref:System.IFormatProvider> está activada de manera el <xref:System.DateTime> tipo.

[!code-csharp[FxCop.Globalization.IFormatProvider#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_2.cs)]

Este ejemplo produce el siguiente resultado:

```txt
6/4/1900 12:15:12 PM
06/04/1900 12:15:12
```

## <a name="related-rules"></a>Reglas relacionadas

- [CA1305: Especificar IFormatProvider](../code-quality/ca1305-specify-iformatprovider.md)

## <a name="see-also"></a>Vea también

- [Uso de la clase CultureInfo](/dotnet/standard/globalization-localization/globalization#Cultures)