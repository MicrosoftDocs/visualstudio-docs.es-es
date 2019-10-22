---
title: 'CA1056: las propiedades URI no deben ser cadenas | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UriPropertiesShouldNotBeStrings
- CA1056
helpviewer_keywords:
- UriPropertiesShouldNotBeStrings
- CA1056
ms.assetid: fdc99d29-0904-4a65-baa8-4f76833c953e
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d9d89f1e8622e4d19fdb3a1c6bac9a6b4f3d7795
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603084"
---
# <a name="ca1056-uri-properties-should-not-be-strings"></a>CA1056: Las propiedades URI no deben ser cadenas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UriPropertiesShouldNotBeStrings|
|Identificador de comprobación|CA1056|
|Categoría|Microsoft. Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo declara una propiedad de cadena cuyo nombre contiene "URI", "URI", "urn", "urn", "URL" o "URL".

## <a name="rule-description"></a>Descripción de la regla
 Esta regla divide el nombre de la propiedad en tokens según la Convención de mayúsculas y minúsculas Pascal y comprueba si cada token es igual a "URI", "URI", "urn", "urn", "URL" o "URL". Si hay una coincidencia, la regla supone que la propiedad representa un identificador uniforme de recursos (URI). Las representaciones de cadena de identificadores URI tienen tendencia a analizar y codificar errores, por lo que pueden crear puntos vulnerables en la seguridad. La clase <xref:System.Uri?displayProperty=fullName> proporciona estos servicios de forma segura.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambie la propiedad a un tipo <xref:System.Uri>.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si la propiedad no representa un URI.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un tipo, `ErrorProne`, que infringe esta regla, y un tipo, `SaferWay`, que cumple la regla.

 [!code-cpp[FxCop.Design.UriNotString#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/cpp/FxCop.Design.UriNotString.cpp#1)]
 [!code-csharp[FxCop.Design.UriNotString#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/cs/FxCop.Design.UriNotString.cs#1)]
 [!code-vb[FxCop.Design.UriNotString#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/vb/FxCop.Design.UriNotString.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1054: Los parámetros de URI no deben ser cadenas](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055: Los valores devueltos URI no deben ser cadenas](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)

 [CA2234: Pase objetos System.Uri en lugar de cadenas](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1057: Las sobrecargas URI de cadena llaman a sobrecargas System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)
