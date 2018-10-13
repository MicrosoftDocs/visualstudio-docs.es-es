---
title: 'CA1055: URI devuelven valores no deben ser cadenas | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1055
- UriReturnValuesShouldNotBeStrings
helpviewer_keywords:
- UriReturnValuesShouldNotBeStrings
- CA1055
ms.assetid: 40e39873-7872-4988-8195-9eb0ade9ece0
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: cb00e9b22c329118d59e7b1d552d29f0fd2a82eb
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49211684"
---
# <a name="ca1055-uri-return-values-should-not-be-strings"></a>CA1055: Los valores devueltos URI no deben ser cadenas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|UriReturnValuesShouldNotBeStrings|
|Identificador de comprobación|CA1055|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 El nombre de un método contiene "uri", "Uri", "urn", "Urn", "url" o "Url" y el método devuelve una cadena.

## <a name="rule-description"></a>Descripción de la regla
 Esta regla divide el nombre del método en tokens según la convención Pascal de mayúsculas y minúsculas y comprueba si cada token es igual a "uri", "Uri", "urn", "Urn", "url" o "Url". Si hay una coincidencia, la regla supone que el método devuelve un identificador uniforme de recursos (URI). Las representaciones de cadena de identificadores URI tienen tendencia a analizar y codificar errores, por lo que pueden crear puntos vulnerables en la seguridad. La <xref:System.Uri?displayProperty=fullName> clase proporciona estos servicios de forma segura.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambie el tipo de valor devuelto para un <xref:System.Uri>.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si el valor devuelto no representa un URI.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un tipo, `ErrorProne`, que infringe esta regla y un tipo, `SaferWay`, que cumple la regla.

 [!code-cpp[FxCop.Design.UriNotString#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/cpp/FxCop.Design.UriNotString.cpp#1)]
 [!code-csharp[FxCop.Design.UriNotString#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/cs/FxCop.Design.UriNotString.cs#1)]
 [!code-vb[FxCop.Design.UriNotString#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/vb/FxCop.Design.UriNotString.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1056: Las propiedades URI no deben ser cadenas](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1054: Los parámetros de URI no deben ser cadenas](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA2234: Pase objetos System.Uri en lugar de cadenas](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1057: Las sobrecargas URI de cadena llaman a sobrecargas System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)



