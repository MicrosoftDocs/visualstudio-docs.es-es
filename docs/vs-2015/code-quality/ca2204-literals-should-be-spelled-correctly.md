---
title: 'CA2204: los literales deben estar escritos correctamente | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d3e94f308936f898e555b1ad38e6a9d50051a276
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659538"
---
# <a name="ca2204-literals-should-be-spelled-correctly"></a>CA2204: Debe escribir correctamente los literales
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|LiteralsShouldBeSpelledCorrectly|
|Identificador de comprobación|CA2204|
|Categoría|Microsoft. Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 Un método pasa una cadena literal a que se utiliza en un parámetro o propiedad que requiere una cadena localizada y la cadena literal contiene una o varias palabras que la biblioteca de corrector ortográfico de Microsoft no reconoce.

## <a name="rule-description"></a>Descripción de la regla
 Esta regla comprueba una cadena literal que se pasa como un valor a un parámetro o propiedad cuando se cumple uno o varios de los casos siguientes:

- El atributo <xref:System.ComponentModel.LocalizableAttribute> del parámetro o propiedad está establecido en true.

- El nombre de la propiedad o el parámetro contiene "Text", "message" o "Caption".

- El nombre del parámetro de cadena que se pasa a un método Console. Write o Console. WriteLine es "Value" o "format".

  Esta regla analiza la cadena literal en palabras, acortando las palabras compuestas y comprueba la ortografía de cada palabra o token. Para obtener información sobre el algoritmo de análisis, vea [CA1704: los identificadores deberían estar escritos correctamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

  De forma predeterminada, se usa la versión en inglés (en) del corrector ortográfico.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, corrija la ortografía de la palabra o agregue la palabra a un diccionario personalizado. Para obtener información sobre cómo usar diccionarios personalizados, vea [Cómo: personalizar el Diccionario de análisis de código](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla. Las palabras escritas correctamente reducen la curva de aprendizaje necesaria para las nuevas bibliotecas de software.

## <a name="related-rules"></a>Reglas relacionadas
 [CA1704: Los identificadores deberían tener la ortografía correcta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

 [CA1703: Las cadenas de recursos deberían tener la ortografía correcta](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)
