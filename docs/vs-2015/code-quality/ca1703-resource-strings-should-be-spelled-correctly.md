---
title: 'CA1703: las cadenas de recursos deberían estar escritas correctamente | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ResourceStringsShouldBeSpelledCorrectly
- CA1703
helpviewer_keywords:
- CA1703
- ResourceStringsShouldBeSpelledCorrectly
ms.assetid: 693f4970-f512-40cb-ae3b-a0f3a5c6d6f1
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2e720c1c491e88b6d89fb4b1f0175e8bc8a56e27
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544058"
---
# <a name="ca1703-resource-strings-should-be-spelled-correctly"></a>CA1703: La ortografía de las cadenas de recursos debe ser correcta
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|ResourceStringsShouldBeSpelledCorrectly|
|Identificador de comprobación|CA1703|
|Category|Microsoft.Naming|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Causa
 Una cadena de recurso contiene una o varias palabras que la biblioteca de correctores ortográficos de Microsoft no reconoce.

## <a name="rule-description"></a>Descripción de la regla
 Esta regla analiza la cadena de recursos en palabras (con tokens compuestos de palabras compuestas) y comprueba la ortografía de cada palabra o token. Para obtener información sobre el algoritmo de análisis, vea [CA1704: los identificadores deberían estar escritos correctamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

 De forma predeterminada, se usa la versión en inglés (en) del corrector ortográfico.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, use palabras completas que estén escritas correctamente o agregue las palabras a un diccionario personalizado. Para obtener información sobre cómo usar diccionarios personalizados, vea [CA1704: los identificadores deberían estar escritos correctamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla. Las palabras escritas correctamente reducen el tiempo necesario para obtener información sobre las nuevas bibliotecas de software.

## <a name="related-rules"></a>Reglas relacionadas
 [CA1701: En las palabras compuestas de la cadena de recursos se deben utilizar mayúsculas y minúsculas correctamente](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

 [CA1704: La ortografía de los identificadores debe ser correcta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

 [CA2204: Los literales deben estar escritos correctamente](../code-quality/ca2204-literals-should-be-spelled-correctly.md)
