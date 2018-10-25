---
title: 'CA1057: Cadena las sobrecargas URI llaman a sobrecargas System.Uri | Microsoft Docs'
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
- CA1057
- StringUriOverloadsCallSystemUriOverloads
helpviewer_keywords:
- StringUriOverloadsCallSystemUriOverloads
- CA1057
ms.assetid: ef1e983e-9ca7-404b-82d7-65740ba0ce20
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e948e91a0559034e688e029eb5ba227a8dd343c2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49920513"
---
# <a name="ca1057-string-uri-overloads-call-systemuri-overloads"></a>CA1057: Las sobrecargas URI de cadena llaman a sobrecargas System.Uri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|StringUriOverloadsCallSystemUriOverloads|
|Identificador de comprobación|CA1057|
|Categoría|Microsoft.Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Un tipo declara sobrecargas del método que se diferencian únicamente por la sustitución de un parámetro de cadena con un <xref:System.Uri?displayProperty=fullName> parámetro y la sobrecarga que toma el parámetro de cadena no llama a la sobrecarga que toma el <xref:System.Uri> parámetro.

## <a name="rule-description"></a>Descripción de la regla
 Dado que las sobrecargas se diferencian únicamente por la cadena /<xref:System.Uri> parámetro, se supone que la cadena para representar un identificador uniforme de recursos (URI). Las representaciones de cadena de identificadores URI tienen tendencia a analizar y codificar errores, por lo que pueden crear puntos vulnerables en la seguridad. La <xref:System.Uri> clase proporciona estos servicios de forma segura. Para obtener las ventajas de la <xref:System.Uri> (clase), debe llamar la sobrecarga de la cadena la <xref:System.Uri> sobrecargar utilizando el argumento de cadena.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Volver a implementar el método que usa la representación de cadena del URI para que crea una instancia de la <xref:System.Uri> clase utilizando el argumento de cadena y, a continuación, pasa el <xref:System.Uri> objeto a la sobrecarga que tiene el <xref:System.Uri> parámetro.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si el parámetro de cadena no representa un URI.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra una sobrecarga de la cadena correctamente implementado.

 [!code-cpp[FxCop.Design.CallUriOverload#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/cpp/FxCop.Design.CallUriOverload.cpp#1)]
 [!code-csharp[FxCop.Design.CallUriOverload#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/cs/FxCop.Design.CallUriOverload.cs#1)]
 [!code-vb[FxCop.Design.CallUriOverload#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/vb/FxCop.Design.CallUriOverload.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA2234: Pase objetos System.Uri en lugar de cadenas](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1056: Las propiedades URI no deben ser cadenas](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1054: Los parámetros de URI no deben ser cadenas](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055: Los valores devueltos URI no deben ser cadenas](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)



