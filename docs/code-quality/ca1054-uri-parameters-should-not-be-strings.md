---
title: "CA1054: Los parámetros de URI no deben ser cadenas | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1054
- UriParametersShouldNotBeStrings
helpviewer_keywords:
- CA1054
- UriParametersShouldNotBeStrings
ms.assetid: 8e99d72b-a658-47a7-8dd5-9784ce2c30b8
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 61f3f42e8a873f4be2873798f9137fbc22feb8fb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="ca1054-uri-parameters-should-not-be-strings"></a>CA1054: Los parámetros de URI no deben ser cadenas
|||  
|-|-|  
|TypeName|UriParametersShouldNotBeStrings|  
|Identificador de comprobación|CA1054|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Problemático|  
  
## <a name="cause"></a>Motivo  
 Un tipo declara un método con un parámetro de cadena cuyo nombre contiene "uri", "Uri", "urn", "Urn", "url" o "Url" y el tipo no declara una sobrecarga correspondiente que toma un <xref:System.Uri?displayProperty=fullName> parámetro.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Esta regla divide el nombre del parámetro en tokens basándose en la convención camel de mayúsculas y minúsculas y comprueba si cada token es igual a "uri", "Uri", "urn", "Urn", "url" o "Url". Si hay una coincidencia, la regla supone que el parámetro representa un identificador uniforme de recursos (URI). Las representaciones de cadena de identificadores URI tienen tendencia a analizar y codificar errores, por lo que pueden crear puntos vulnerables en la seguridad. Si un método toma una representación de cadena de un identificador URI, una correspondiente debe proporcionarse la sobrecarga que toma una instancia de la <xref:System.Uri> (clase), que proporciona estos servicios de una manera segura.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, cambie el parámetro a un <xref:System.Uri> escriba; se trata de un cambio importante. Como alternativa, proporcione una sobrecarga del método que toma un <xref:System.Uri> parámetro; se trata de un cambio sin interrupción.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla si el parámetro no representa un URI.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra un tipo, `ErrorProne`, que infringe esta regla y un tipo, `SaferWay`, que cumple la regla.  
  
 [!code-csharp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1054-uri-parameters-should-not-be-strings_1.cs)]
 [!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1054-uri-parameters-should-not-be-strings_1.vb)]
 [!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1054-uri-parameters-should-not-be-strings_1.cpp)]  
  
## <a name="related-rules"></a>Reglas relacionadas  
 [CA1056: Las propiedades URI no deben ser cadenas](../code-quality/ca1056-uri-properties-should-not-be-strings.md)  
  
 [CA1055: Los valores devueltos URI no deben ser cadenas](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)  
  
 [CA2234: Pase objetos System.Uri en lugar de cadenas](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)  
  
 [CA1057: Las sobrecargas URI de cadena llaman a sobrecargas System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)