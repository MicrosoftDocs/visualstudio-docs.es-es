---
title: 'CA1057: Las sobrecargas URI de cadena llaman a sobrecargas System.Uri'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4a2e140b4b861e2666350154d861814378f5d115
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="ca1057-string-uri-overloads-call-systemuri-overloads"></a>CA1057: Las sobrecargas URI de cadena llaman a sobrecargas System.Uri
|||
|-|-|
|TypeName|StringUriOverloadsCallSystemUriOverloads|
|Identificador de comprobación|CA1057|
|Categoría|Microsoft.Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Un tipo declara sobrecargas de método que solo difieren en el reemplazo de un parámetro de cadena con un <xref:System.Uri?displayProperty=fullName> parámetro y la sobrecarga que toma el parámetro de cadena no llama a la sobrecarga que toma el <xref:System.Uri> parámetro.

## <a name="rule-description"></a>Descripción de la regla
 Dado que las sobrecargas solamente se distinguen por la cadena /<xref:System.Uri> parámetro, se supone que la cadena para representar un identificador uniforme de recursos (URI). Las representaciones de cadena de identificadores URI tienen tendencia a analizar y codificar errores, por lo que pueden crear puntos vulnerables en la seguridad. La <xref:System.Uri> clase proporciona estos servicios de una manera segura. Para obtener las ventajas de la <xref:System.Uri> (clase), debe llamar la sobrecarga de la cadena la <xref:System.Uri> sobrecargar mediante el argumento de cadena.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Volver a implementar el método que utiliza la representación de cadena del URI para que crea una instancia de la <xref:System.Uri> clase utilizando el argumento de cadena y, a continuación, pasa el <xref:System.Uri> objeto a la sobrecarga que tiene el <xref:System.Uri> parámetro.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si el parámetro de cadena no representa un URI.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra una sobrecarga de cadena correctamente implementada.

 [!code-csharp[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/CSharp/ca1057-string-uri-overloads-call-system-uri-overloads_1.cs)]
 [!code-cpp[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/CPP/ca1057-string-uri-overloads-call-system-uri-overloads_1.cpp)]
 [!code-vb[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/VisualBasic/ca1057-string-uri-overloads-call-system-uri-overloads_1.vb)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA2234: Pase objetos System.Uri en lugar de cadenas](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1056: Las propiedades URI no deben ser cadenas](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1054: Los parámetros de URI no deben ser cadenas](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055: Los valores devueltos URI no deben ser cadenas](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)