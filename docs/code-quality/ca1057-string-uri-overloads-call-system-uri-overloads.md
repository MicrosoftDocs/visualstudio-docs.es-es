---
title: 'CA1057: Las sobrecargas URI de cadena llaman a sobrecargas System.Uri'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1057
- StringUriOverloadsCallSystemUriOverloads
helpviewer_keywords:
- StringUriOverloadsCallSystemUriOverloads
- CA1057
ms.assetid: ef1e983e-9ca7-404b-82d7-65740ba0ce20
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 41d3db6e4807c77236868e3ab5746da971ddce6c
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922489"
---
# <a name="ca1057-string-uri-overloads-call-systemuri-overloads"></a>CA1057: Las sobrecargas URI de cadena llaman a sobrecargas System.Uri

|||
|-|-|
|TypeName|StringUriOverloadsCallSystemUriOverloads|
|Identificador de comprobación|CA1057|
|Categoría|Microsoft.Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Causa

Un tipo declara sobrecargas de método que solo difieren en el reemplazo de un parámetro de <xref:System.Uri?displayProperty=fullName> cadena con un parámetro, y la sobrecarga que toma el parámetro de cadena no llama a la <xref:System.Uri> sobrecarga que toma el parámetro.

## <a name="rule-description"></a>Descripción de la regla
Dado que las sobrecargas solo difieren en <xref:System.Uri> la cadena o el parámetro, se supone que la cadena representa un identificador uniforme de recursos (URI). Las representaciones de cadena de identificadores URI tienen tendencia a analizar y codificar errores, por lo que pueden crear puntos vulnerables en la seguridad. La <xref:System.Uri> clase proporciona estos servicios de forma segura. Para aprovechar las ventajas de la <xref:System.Uri> clase, la sobrecarga de la cadena debe <xref:System.Uri> llamar a la sobrecarga mediante el argumento de cadena.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Vuelva a implementar el método que usa la representación de cadena del URI para que cree una instancia de la <xref:System.Uri> clase mediante el argumento de cadena y, a continuación <xref:System.Uri> , pase el objeto a la sobrecarga <xref:System.Uri> que tiene el parámetro.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
Es seguro suprimir una advertencia de esta regla si el parámetro de cadena no representa un URI.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra una sobrecarga de cadena implementada correctamente.

[!code-csharp[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/CSharp/ca1057-string-uri-overloads-call-system-uri-overloads_1.cs)]
[!code-cpp[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/CPP/ca1057-string-uri-overloads-call-system-uri-overloads_1.cpp)]
[!code-vb[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/VisualBasic/ca1057-string-uri-overloads-call-system-uri-overloads_1.vb)]

## <a name="related-rules"></a>Reglas relacionadas
[CA2234: Pasar objetos System. Uri en lugar de cadenas](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

[CA1056: Las propiedades URI no deben ser cadenas](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

[CA1054: Los parámetros de URI no deben ser cadenas](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

[CA1055: Los valores devueltos de URI no deben ser cadenas](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)