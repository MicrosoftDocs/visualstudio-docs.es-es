---
title: 'CA2243: los literales de cadena de atributo se deben analizar correctamente | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2243
- AttributeStringLiteralsShouldParseCorrectly
helpviewer_keywords:
- AttributeStringLiteralsShouldParseCorrectly
- CA2243
ms.assetid: bfadb366-379d-4ee4-b17b-c4a09bf1106b
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 09e932651576f9b6d595657ad024b8f2697ad016
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85535751"
---
# <a name="ca2243-attribute-string-literals-should-parse-correctly"></a>CA2243: Los literales de cadena de atributo se deben analizar correctamente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|AttributeStringLiteralsShouldParseCorrectly|
|Identificador de comprobación|CA2243|
|Category|Microsoft. Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Causa
 El parámetro de literal de cadena de un atributo no se analiza correctamente para una dirección URL, un GUID o una versión.

## <a name="rule-description"></a>Descripción de la regla
 Puesto que los atributos se derivan de <xref:System.Attribute?displayProperty=fullName> y los atributos se usan en tiempo de compilación, solo se pueden pasar valores constantes a sus constructores. Los parámetros de atributo que deben representar direcciones URL, GUID y versiones no se pueden escribir como <xref:System.Uri?displayProperty=fullName> , <xref:System.Guid?displayProperty=fullName> y <xref:System.Version?displayProperty=fullName> , porque estos tipos no se pueden representar como constantes. En su lugar, deben representarse mediante cadenas.

 Dado que el parámetro se escribe como una cadena, es posible que se pase un parámetro con un formato incorrecto en tiempo de compilación.

 Esta regla usa una heurística de nomenclatura para buscar parámetros que representan un identificador uniforme de recursos (URI), un identificador único global (GUID) o una versión y comprueba que el valor pasado es correcto.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Cambie la cadena de parámetro a una dirección URL, un GUID o una versión correctos.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si el parámetro no representa una dirección URL, un GUID o una versión.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra el código para el AssemblyFileVersionAttribute que infringe esta regla.

 [!code-csharp[FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly/cs/FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly.cs#1)]

 La regla se desencadena con lo siguiente:

- Los parámetros que contienen ' version ' y no se pueden analizar en System. version.

- Los parámetros que contienen "GUID" y no se pueden analizar en System. GUID.

- Los parámetros que contienen "URI", "urn" o "URL" y no se pueden analizar en System. Uri.

## <a name="see-also"></a>Consulte también
 [CA1054: Los parámetros de URI no deben ser cadenas](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)
