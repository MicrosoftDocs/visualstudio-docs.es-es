---
title: 'CA1055: Los valores devueltos URI no deben ser cadenas'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1055
- UriReturnValuesShouldNotBeStrings
helpviewer_keywords:
- UriReturnValuesShouldNotBeStrings
- CA1055
ms.assetid: 40e39873-7872-4988-8195-9eb0ade9ece0
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 5391c940cc6d9eef7a6541a855541bb05f60d1b2
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57867792"
---
# <a name="ca1055-uri-return-values-should-not-be-strings"></a>CA1055: Los valores devueltos URI no deben ser cadenas

|||
|-|-|
|TypeName|UriReturnValuesShouldNotBeStrings|
|Identificador de comprobación|CA1055|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo

El nombre de un método contiene "uri", "Uri", "urn", "Urn", "url" o "Url" y el método devuelve una cadena.

De forma predeterminada, esta regla solo se examina los métodos públicos, pero se trata de [configurable](#configurability).

## <a name="rule-description"></a>Descripción de la regla

Esta regla divide el nombre del método en tokens según la convención Pascal de mayúsculas y minúsculas y comprueba si cada token es igual a "uri", "Uri", "urn", "Urn", "url" o "Url". Si hay una coincidencia, la regla supone que el método devuelve un identificador uniforme de recursos (URI). Las representaciones de cadena de identificadores URI tienen tendencia a analizar y codificar errores, por lo que pueden crear puntos vulnerables en la seguridad. La <xref:System.Uri?displayProperty=fullName> clase proporciona estos servicios de forma segura.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, cambie el tipo de valor devuelto para un <xref:System.Uri>.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

Es seguro suprimir una advertencia de esta regla si el valor devuelto no representa un URI.

## <a name="configurability"></a>Capacidad de configuración

Si ejecuta esta regla de [analizadores de FxCop](install-fxcop-analyzers.md) (y no a través de análisis de código estático), puede configurar qué partes de su código base para ejecutar esta regla en, en función de su accesibilidad. Por ejemplo, para especificar que debe ejecutarse la regla sólo con respecto a la superficie de API no públicos, agregue el siguiente par clave-valor a un archivo .editorconfig en el proyecto:

```
dotnet_code_quality.ca1055.api_surface = private, internal
```

Puede configurar esta opción para simplemente esta regla, para todas las reglas o para todas las reglas de esta categoría (diseño). Para obtener más información, consulte [analizadores de FxCop configurar](configure-fxcop-analyzers.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra un tipo, `ErrorProne`, que infringe esta regla y un tipo, `SaferWay`, que cumple la regla.

[!code-csharp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1055-uri-return-values-should-not-be-strings_1.cs)]
[!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1055-uri-return-values-should-not-be-strings_1.vb)]
[!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1055-uri-return-values-should-not-be-strings_1.cpp)]

## <a name="related-rules"></a>Reglas relacionadas

- [CA1056: Las propiedades URI no deben ser cadenas](../code-quality/ca1056-uri-properties-should-not-be-strings.md)
- [CA1054: Los parámetros de URI no deben ser cadenas](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)
- [CA2234: Pase objetos System.Uri en lugar de cadenas](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)
- [CA1057: Las sobrecargas URI de cadena llaman a sobrecargas System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)