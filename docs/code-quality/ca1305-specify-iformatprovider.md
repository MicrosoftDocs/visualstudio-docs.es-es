---
title: 'CA1305: Especificar IFormatProvider'
ms.date: 06/30/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- SpecifyIFormatProvider
- CA1305
helpviewer_keywords:
- CA1305
- SpecifyIFormatProvider
ms.assetid: fb34ed9a-4eab-47cc-8eef-3068a4a1397e
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 55ecfa146958819092c51055e039f57e8c1b3f6e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55018714"
---
# <a name="ca1305-specify-iformatprovider"></a>CA1305: Especificar IFormatProvider

|||
|-|-|
|TypeName|SpecifyIFormatProvider|
|Identificador de comprobación|CA1305|
|Categoría|Microsoft.Globalization|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo

Un método o constructor llama a uno o más miembros que tienen sobrecargas que aceptan un <xref:System.IFormatProvider?displayProperty=fullName> parámetro y el método o constructor no llama a la sobrecarga que toma el <xref:System.IFormatProvider> parámetro.

Esta regla omite las llamadas a métodos de .NET Framework que se documentan omitiendo el <xref:System.IFormatProvider> parámetro. La regla también omite los métodos siguientes:

- <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>

## <a name="rule-description"></a>Descripción de la regla

Cuando un <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> o <xref:System.IFormatProvider> objeto no se proporciona, el valor predeterminado proporcionado por el miembro sobrecargado podría no tener el efecto deseado en todas las configuraciones regionales. Además, los miembros de .NET Framework eligen la referencia cultural predeterminada y formato basado en suposiciones que pueden no ser correctas para su código. Para asegurarse de que el código funciona según lo esperado para sus escenarios, debería proporcionar información de referencia cultural específica según las siguientes directrices:

- Si el valor se mostrará al usuario, use la referencia cultural actual. Vea <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.

- Si el valor se almacenará y acceso a software (guardado en un archivo o base de datos), use la referencia cultural invariable. Vea <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.

- Si no conoce el destino del valor, tiene el consumidor de datos o proveedor de especificar la referencia cultural.

Aunque el comportamiento predeterminado del miembro sobrecargado es adecuado para sus necesidades, es mejor llamar explícitamente a la sobrecarga de la referencia cultural específica para que el código sea más fácil de mantener y documenten por sí mismos.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, use la sobrecarga que toma un <xref:System.IFormatProvider> argumento. O bien, use un [C# cadena interpolada](/dotnet/csharp/tutorials/string-interpolation) y páselo a la <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> método.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

Es seguro suprimir una advertencia de esta regla cuando se tiene la certeza de que el formato predeterminado es la elección correcta y mantención de código no es una prioridad de desarrollo importante.

## <a name="example"></a>Ejemplo

En el código siguiente, la `example1` cadena infringe la regla CA1305. El `example2` cadena cumple la regla CA1305 pasando <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>, que implementa <xref:System.IFormatProvider>a <xref:System.String.Format(System.IFormatProvider,System.String,System.Object)?displayProperty=nameWithType>. El `example3` cadena cumple la regla CA1305 pasando una cadena interpolada a <xref:System.FormattableString.Invariant%2A?displayProperty=fullName]>.

```csharp
string name = "Georgette";

// Violates CA1305
string example1 = String.Format("Hello {0}", name);

// Satisfies CA1305
string example2 = String.Format(CultureInfo.CurrentCulture, "Hello {0}", name);

// Satisfies CA1305
string example3 = FormattableString.Invariant($"Hello {name}");
```

## <a name="related-rules"></a>Reglas relacionadas

- [CA1304: Especificar CultureInfo](../code-quality/ca1304-specify-cultureinfo.md)

## <a name="see-also"></a>Vea también

- [Uso de la clase CultureInfo](/dotnet/standard/globalization-localization/globalization#Cultures)