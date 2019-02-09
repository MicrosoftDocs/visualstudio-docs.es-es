---
title: 'CA1056: Las propiedades URI no deben ser cadenas'
ms.date: 11/04/2016
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
ms.openlocfilehash: 529b0d360c3301d7bb3eee79911e5d3fbb5d3af6
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55938924"
---
# <a name="ca1056-uri-properties-should-not-be-strings"></a>CA1056: Las propiedades URI no deben ser cadenas

|||
|-|-|
|TypeName|UriPropertiesShouldNotBeStrings|
|Identificador de comprobación|CA1056|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo declara una propiedad de cadena cuyo nombre contiene "uri", "Uri", "urn", "Urn", "url" o "Url".

## <a name="rule-description"></a>Descripción de la regla
 Esta regla divide el nombre de propiedad en tokens según la convención Pascal de mayúsculas y minúsculas y comprueba si cada token es igual a "uri", "Uri", "urn", "Urn", "url" o "Url". Si hay una coincidencia, la regla supone que la propiedad representa un identificador uniforme de recursos (URI). Las representaciones de cadena de identificadores URI tienen tendencia a analizar y codificar errores, por lo que pueden crear puntos vulnerables en la seguridad. La <xref:System.Uri?displayProperty=fullName> clase proporciona estos servicios de forma segura.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambie la propiedad a un <xref:System.Uri> tipo.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si la propiedad no representa un URI.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un tipo, `ErrorProne`, que infringe esta regla y un tipo, `SaferWay`, que cumple la regla.

 [!code-csharp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1056-uri-properties-should-not-be-strings_1.cs)]
 [!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1056-uri-properties-should-not-be-strings_1.vb)]
 [!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1056-uri-properties-should-not-be-strings_1.cpp)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1054: Los parámetros de URI no deben ser cadenas](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055: URI devuelven valores no deben ser cadenas](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)

 [CA2234: Pase objetos System.Uri en lugar de cadenas](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1057: Las sobrecargas URI de cadena llaman a sobrecargas System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)