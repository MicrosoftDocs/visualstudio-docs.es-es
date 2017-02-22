---
title: "CA2243: Los literales de cadena de atributo se deben analizar correctamente | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2243"
  - "AttributeStringLiteralsShouldParseCorrectly"
helpviewer_keywords: 
  - "AttributeStringLiteralsShouldParseCorrectly"
  - "CA2243"
ms.assetid: bfadb366-379d-4ee4-b17b-c4a09bf1106b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2243: Los literales de cadena de atributo se deben analizar correctamente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AttributeStringLiteralsShouldParseCorrectly|  
|Identificador de comprobación|CA2243|  
|Categoría|Microsoft.Usage|  
|Cambio problemático|No|  
  
## Motivo  
 El parámetro de literal de cadena de un atributo no se analiza correctamente para una dirección URL, un GUID o una versión.  
  
## Descripción de la regla  
 Dado que los atributos se derivan de <xref:System.Attribute?displayProperty=fullName> y se utilizan en tiempo de compilación, sólo se pueden pasar valores constantes a sus constructores.  Los parámetros de atributo que deben representar direcciones URL, GUID y versiones no pueden ser de tipo <xref:System.Uri?displayProperty=fullName>, <xref:System.Guid?displayProperty=fullName> ni <xref:System.Version?displayProperty=fullName>, porque estos tipos no se pueden representar como constantes.  Deben representarse mediante cadenas.  
  
 Dado que el parámetro es un parámetro de cadena, es posible que se pase un parámetro con formato incorrecto en tiempo de compilación.  
  
 Esta regla utiliza una heurística de nomenclatura para buscar los parámetros que representen un identificador uniforme de recursos \(URI\), un identificador único global \(GUID\) o una versión, y comprueba que el valor pasado es correcto.  
  
## Cómo corregir infracciones  
 Cambie la cadena de parámetro a una dirección URL, un GUID o una versión con el formato correcto.  
  
## Cuándo suprimir advertencias  
 Puede suprimirse de forma segura una advertencia de esta regla si el parámetro no representa una dirección URL, un GUID o una versión.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra código para AssemblyFileVersionAttribute que infringe esta regla.  
  
 [!code-cs[FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly#1](../code-quality/codesnippet/CSharp/ca2243-attribute-string-literals-should-parse-correctly_1.cs)]  
  
 Los siguientes parámetros desencadenan la regla:  
  
-   Parámetros que contienen 'version' y no se pueden analizar como System.Version.  
  
-   Parámetros que contienen 'guid' y no se pueden analizar como System.Guid.  
  
-   Parámetros que contienen 'uri', 'urn' o 'url' y no se pueden analizar como System.Uri.  
  
## Vea también  
 [CA1054: Los parámetros de URI no deben ser cadenas](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)