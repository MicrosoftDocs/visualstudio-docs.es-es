---
title: 'CA2234: pasar objetos System. Uri en lugar de cadenas | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PassSystemUriObjectsInsteadOfStrings
- CA2234
helpviewer_keywords:
- CA2234
- PassSystemUriObjectsInsteadOfStrings
ms.assetid: 14616b37-74c4-4286-b051-115d00aceb5f
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0ce5c076260886def089118a4d7211d75e0185c0
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545215"
---
# <a name="ca2234-pass-systemuri-objects-instead-of-strings"></a>CA2234: Pasar objetos System.Uri en lugar de cadenas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Valor|
|-|-|
|TypeName|PassSystemUriObjectsInsteadOfStrings|
|Identificador de comprobación|CA2234|
|Categoría|Microsoft. Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Causa
 Se realiza una llamada a un método que tiene un parámetro de cadena cuyo nombre contiene "URI", "URI", "urn", "urn", "URL" o "URL". y el tipo declarativo del método contiene una sobrecarga de método correspondiente que tiene un <xref:System.Uri?displayProperty=fullName> parámetro.

## <a name="rule-description"></a>Descripción de la regla
 Un nombre de parámetro se divide en tokens según la Convención de mayúsculas y minúsculas Camel y, a continuación, se comprueba cada token para ver si es igual a "URI", "URI", "urn", "urn", "URL" o "URL". Si hay una coincidencia, se supone que el parámetro representa un identificador uniforme de recursos (URI). Las representaciones de cadena de identificadores URI tienen tendencia a analizar y codificar errores, por lo que pueden crear puntos vulnerables en la seguridad. La <xref:System.Uri> clase proporciona estos servicios de forma segura. Cuando hay una opción entre dos sobrecargas que solo difieren en cuanto a la representación de un URI, el usuario debe elegir la sobrecarga que toma un <xref:System.Uri> argumento.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, llame a la sobrecarga que toma el <xref:System.Uri> argumento.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si el parámetro de cadena no representa un URI.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un método, `ErrorProne` , que infringe la regla y un método, `SaferWay` , que llama correctamente a la <xref:System.Uri> sobrecarga.

 [!code-cpp[FxCop.Usage.PassUri#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.PassUri/cpp/FxCop.Usage.PassUri.cpp#1)]
 [!code-csharp[FxCop.Usage.PassUri#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.PassUri/cs/FxCop.Usage.PassUri.cs#1)]
 [!code-vb[FxCop.Usage.PassUri#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.PassUri/vb/FxCop.Usage.PassUri.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1057: Las sobrecargas URI de cadena llaman a sobrecargas System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)

 [CA1056: Las propiedades URI no deben ser cadenas](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1054: Los parámetros de URI no deben ser cadenas](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055: Los valores devueltos URI no deben ser cadenas](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)
