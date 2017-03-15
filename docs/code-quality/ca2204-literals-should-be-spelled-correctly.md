---
title: "CA2204: Debe escribir correctamente los literales | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Literals should be spelled correctly"
  - "CA2204"
  - "LiteralsShouldBeSpelledCorrectly"
helpviewer_keywords: 
  - "CA2204"
ms.assetid: b0bbcbb6-c92d-4c14-8ef7-9c8b38c791a6
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# CA2204: Debe escribir correctamente los literales
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|LiteralsShouldBeSpelledCorrectly|  
|Identificador de comprobación|CA2204|  
|Categoría|Microsoft.Usage|  
|Cambio problemático|No|  
  
## Motivo  
 Un método pasa una cadena literal que se utiliza en un parámetro o propiedad que requiere una cadena adaptada y la cadena literal contiene una o más palabras que no son reconocidas por la biblioteca del corrector ortográfico de Microsoft.  
  
## Descripción de la regla  
 Esta regla comprueba una cadena literal que se pasa como un valor a un parámetro o propiedad cuando uno o varios de los casos siguientes son verdaderos:  
  
-   El atributo <xref:System.ComponentModel.LocalizableAttribute> del parámetro o propiedad está establecido en true.  
  
-   El parámetro o el nombre de propiedad contiene "Text", "Message" o "Caption".  
  
-   El nombre del parámetro de cadena que se pasa a un método Console.Write o Console.WriteLine es "value" o "format".  
  
 Esta regla analiza la cadena literal en palabras, convierte en tokens las palabras compuestas y comprueba la ortografía de cada palabra o token.  Para obtener información sobre el algoritmo de análisis, vea [CA1704: Los identificadores deberían tener la ortografía correcta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).  
  
 De forma predeterminada, se utiliza la versión inglesa \(en\) del corrector ortográfico.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, corrija la ortografía de la palabra o agregue la palabra a un diccionario personalizado.  Para obtener información sobre cómo utilizar diccionarios personalizados, vea [Cómo: Personalizar el diccionario de análisis de código](../code-quality/how-to-customize-the-code-analysis-dictionary.md).  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  Las palabras escritas correctamente reducen la curva de aprendizaje necesaria para las nuevas bibliotecas de software.  
  
## Reglas relacionadas  
 [CA1704: Los identificadores deberían tener la ortografía correcta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
 [CA1703: Las cadenas de recursos deberían tener la ortografía correcta](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)