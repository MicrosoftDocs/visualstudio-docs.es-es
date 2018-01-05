---
title: 'CA2204: Deben escribir correctamente los literales | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Literals should be spelled correctly
- CA2204
- LiteralsShouldBeSpelledCorrectly
helpviewer_keywords: CA2204
ms.assetid: b0bbcbb6-c92d-4c14-8ef7-9c8b38c791a6
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ad1fb951f17d223f248c678738070d1c5b70ae7d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="ca2204-literals-should-be-spelled-correctly"></a>CA2204: Debe escribir correctamente los literales
|||  
|-|-|  
|TypeName|LiteralsShouldBeSpelledCorrectly|  
|Identificador de comprobación|CA2204|  
|Categoría|Microsoft.Usage|  
|Cambio problemático|No trascendental|  
  
## <a name="cause"></a>Motivo  
 Un método pasa una cadena literal que se utiliza en un parámetro o una propiedad que requiere una cadena localizada y la cadena literal contiene una o varias palabras que no son reconocidas por la biblioteca de correctores ortográficos de Microsoft.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Esta regla comprueba si una cadena literal que se pasa como un valor a un parámetro o una propiedad cuando uno o varios de los casos siguientes es true:  
  
-   El <xref:System.ComponentModel.LocalizableAttribute> del parámetro o la propiedad está establecido en true.  
  
-   El nombre de parámetro o la propiedad contiene "Text", "Mensaje" o "Título".  
  
-   El nombre del parámetro de cadena que se pasa a un método Console.Write o Console.WriteLine es "value" o "format".  
  
 Esta regla analiza la cadena literal en palabras, convirtiendo las palabras compuestas, tokens y comprueba la ortografía de cada palabra o token. Para obtener información sobre el algoritmo de análisis, consulte [CA1704: los identificadores deberían tener la ortografía correcta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).  
  
 De forma predeterminada, se utiliza la versión de inglés (en) del corrector ortográfico.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, corrija la ortografía de la palabra o agregue la palabra a un diccionario personalizado. Para obtener información sobre cómo usar los diccionarios personalizados, vea [Cómo: personalizar el diccionario de análisis de código](../code-quality/how-to-customize-the-code-analysis-dictionary.md).  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla. Palabras escritas correctamente reducen la curva de aprendizaje necesaria para las nuevas bibliotecas de software.  
  
## <a name="related-rules"></a>Reglas relacionadas  
 [CA1704: Los identificadores deberían tener la ortografía correcta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
 [CA1703: Las cadenas de recursos deberían tener la ortografía correcta](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)