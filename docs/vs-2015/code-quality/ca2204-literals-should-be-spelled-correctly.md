---
title: 'CA2204: Los literales deben estar escritos correctamente | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- Literals should be spelled correctly
- CA2204
- LiteralsShouldBeSpelledCorrectly
helpviewer_keywords:
- CA2204
ms.assetid: b0bbcbb6-c92d-4c14-8ef7-9c8b38c791a6
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a08cb7cee2af51ade4b94dbf675ff83d7da456e2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68142505"
---
# <a name="ca2204-literals-should-be-spelled-correctly"></a>CA2204: Los literales deben estar escritos correctamente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|LiteralsShouldBeSpelledCorrectly|
|Identificador de comprobación|CA2204|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Causa
 Un método pasa una cadena literal que se usa en un parámetro o una propiedad que requiere una cadena traducida y la cadena literal contiene una o varias palabras que no son reconocidas por la biblioteca de correctores ortográficos de Microsoft.

## <a name="rule-description"></a>Descripción de la regla
 Esta regla comprueba si una cadena literal que se pasa como un valor a un parámetro o propiedad cuando uno o varios de los casos siguientes es true:

- El <xref:System.ComponentModel.LocalizableAttribute> atributo del parámetro o la propiedad se establece en true.

- El nombre de parámetro o la propiedad contiene "Text", "Mensaje" o "Título".

- El nombre del parámetro de cadena que se pasa a un método Console.Write o Console.WriteLine es "value" o "format".

  Esta regla analiza la cadena literal en palabras, dividir en tokens las palabras compuestas y comprueba la ortografía de cada palabra o token. Para obtener información sobre el algoritmo de análisis, consulte [CA1704: Deben escribir correctamente los identificadores](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

  De forma predeterminada, se utiliza la versión inglesa (en) del corrector ortográfico.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, corrija la ortografía de la palabra o agregar la palabra a un diccionario personalizado. Para obtener información sobre cómo usar los diccionarios personalizados, vea [Cómo: Personalizar el diccionario de análisis de código](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla. Palabras escritas correctamente reducen la curva de aprendizaje necesaria para las nuevas bibliotecas de software.

## <a name="related-rules"></a>Reglas relacionadas
 [CA1704: Los identificadores deberían tener la ortografía correcta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

 [CA1703: Cadenas de recursos deberían tener la ortografía correcta](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)
