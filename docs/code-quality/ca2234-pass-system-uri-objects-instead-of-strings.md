---
title: 'CA2234: Pase objetos System.Uri en lugar de cadenas'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PassSystemUriObjectsInsteadOfStrings
- CA2234
helpviewer_keywords:
- CA2234
- PassSystemUriObjectsInsteadOfStrings
ms.assetid: 14616b37-74c4-4286-b051-115d00aceb5f
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: fcc7994e67e268aff21af925632d2ee9cf102ff4
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547167"
---
# <a name="ca2234-pass-systemuri-objects-instead-of-strings"></a>CA2234: Pase objetos System.Uri en lugar de cadenas

|||
|-|-|
|TypeName|PassSystemUriObjectsInsteadOfStrings|
|Identificador de comprobación|CA2234|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 Se realiza una llamada a un método que tiene un parámetro de cadena cuyo nombre contiene "uri", "Uri", "urn", "Urn", "url" o "Url"; y el tipo declarativo del método contiene una sobrecarga del método correspondiente que tiene un <xref:System.Uri?displayProperty=fullName> parámetro.

## <a name="rule-description"></a>Descripción de la regla
 Un nombre de parámetro se divide en tokens según la convención camel de mayúsculas y minúsculas, y, a continuación, cada token se comprueba para ver si es igual a "uri", "Uri", "urn", "Urn", "url" o "Url". Si hay una coincidencia, se supone que el parámetro representa un identificador uniforme de recursos (URI). Las representaciones de cadena de identificadores URI tienen tendencia a analizar y codificar errores, por lo que pueden crear puntos vulnerables en la seguridad. La <xref:System.Uri> clase proporciona estos servicios de forma segura. Cuando hay que elegir entre dos sobrecargas que difieren solo relativas a la representación de un URI, el usuario debe elegir la sobrecarga que toma un <xref:System.Uri> argumento.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, llame a la sobrecarga que toma el <xref:System.Uri> argumento.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si el parámetro de cadena no representa un URI.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un método, `ErrorProne`, lo que infringe la regla y un método, `SaferWay`, que llama correctamente a la <xref:System.Uri> de sobrecarga.

 [!code-vb[FxCop.Usage.PassUri#1](../code-quality/codesnippet/VisualBasic/ca2234-pass-system-uri-objects-instead-of-strings_1.vb)]
 [!code-cpp[FxCop.Usage.PassUri#1](../code-quality/codesnippet/CPP/ca2234-pass-system-uri-objects-instead-of-strings_1.cpp)]
 [!code-csharp[FxCop.Usage.PassUri#1](../code-quality/codesnippet/CSharp/ca2234-pass-system-uri-objects-instead-of-strings_1.cs)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1057: Las sobrecargas URI de cadena llaman a sobrecargas System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)

 [CA1056: Las propiedades URI no deben ser cadenas](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1054: Los parámetros de URI no deben ser cadenas](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055: Los valores devueltos URI no deben ser cadenas](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)