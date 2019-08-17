---
title: 'CA1056: Las propiedades URI no deben ser cadenas'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- UriPropertiesShouldNotBeStrings
- CA1056
helpviewer_keywords:
- UriPropertiesShouldNotBeStrings
- CA1056
ms.assetid: fdc99d29-0904-4a65-baa8-4f76833c953e
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 2d9ff79bc7e276e4070a1df1760c0cfde7ed28b1
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547341"
---
# <a name="ca1056-uri-properties-should-not-be-strings"></a>CA1056: Las propiedades URI no deben ser cadenas

|||
|-|-|
|TypeName|UriPropertiesShouldNotBeStrings|
|Identificador de comprobación|CA1056|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa

Un tipo declara una propiedad de cadena cuyo nombre contiene "URI", "URI", "urn", "urn", "URL" o "URL".

De forma predeterminada, esta regla solo examina los tipos visibles externamente, pero esto es [configurable](#configurability).

## <a name="rule-description"></a>Descripción de la regla

Esta regla divide el nombre de la propiedad en tokens según la Convención de mayúsculas y minúsculas Pascal y comprueba si cada token es igual a "URI", "URI", "urn", "urn", "URL" o "URL". Si hay una coincidencia, la regla supone que la propiedad representa un identificador uniforme de recursos (URI). Las representaciones de cadena de identificadores URI tienen tendencia a analizar y codificar errores, por lo que pueden crear puntos vulnerables en la seguridad. La <xref:System.Uri?displayProperty=fullName> clase proporciona estos servicios de forma segura.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, cambie la propiedad a <xref:System.Uri> un tipo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

Es seguro suprimir una advertencia de esta regla si la propiedad no representa un URI.

## <a name="configurability"></a>Configurabilidad

Si está ejecutando esta regla desde los [analizadores de FxCop](install-fxcop-analyzers.md) (y no con el análisis heredado), puede configurar en qué partes del código base ejecutar esta regla, según su accesibilidad. Por ejemplo, para especificar que la regla se debe ejecutar solo en la superficie de API no pública, agregue el siguiente par clave-valor a un archivo. editorconfig en el proyecto:

```ini
dotnet_code_quality.ca1056.api_surface = private, internal
```

Puede configurar esta opción solo para esta regla, para todas las reglas o para todas las reglas de esta categoría (diseño). Para obtener más información, vea [configurar analizadores de FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra un `ErrorProne`tipo,, que infringe esta regla, y un tipo `SaferWay`,, que cumple la regla.

[!code-csharp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1056-uri-properties-should-not-be-strings_1.cs)]
[!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1056-uri-properties-should-not-be-strings_1.vb)]
[!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1056-uri-properties-should-not-be-strings_1.cpp)]

## <a name="related-rules"></a>Reglas relacionadas

- [CA1054: Los parámetros de URI no deben ser cadenas](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)
- [CA1055: Los valores devueltos de URI no deben ser cadenas](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)
- [CA2234: Pasar objetos System. Uri en lugar de cadenas](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)
- [CA1057: Las sobrecargas URI de cadena llaman a sobrecargas System. Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)