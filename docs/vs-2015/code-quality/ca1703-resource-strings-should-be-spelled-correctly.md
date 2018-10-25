---
title: 'CA1703: Las cadenas de recursos deben estar escritas correctamente | Microsoft Docs'
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
- ResourceStringsShouldBeSpelledCorrectly
- CA1703
helpviewer_keywords:
- CA1703
- ResourceStringsShouldBeSpelledCorrectly
ms.assetid: 693f4970-f512-40cb-ae3b-a0f3a5c6d6f1
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e5f5541a048d1434f64bf53e7573fa8288933e4e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49855012"
---
# <a name="ca1703-resource-strings-should-be-spelled-correctly"></a>CA1703: Las cadenas de recursos deberían tener la ortografía correcta
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ResourceStringsShouldBeSpelledCorrectly|
|Identificador de comprobación|CA1703|
|Categoría|Microsoft.Naming|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Una cadena de recurso contiene una o varias palabras que la biblioteca de correctores ortográficos de Microsoft no reconoce.

## <a name="rule-description"></a>Descripción de la regla
 Esta regla analiza la cadena de recurso en palabras (convirtiendo las palabras compuestas en tokens) y comprueba la ortografía de cada palabra o token. Para obtener información sobre el algoritmo de análisis, vea [CA1704: los identificadores deben estar escritos correctamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

 De forma predeterminada, se utiliza la versión inglesa (en) del corrector ortográfico.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, utilice palabras completas que estén escritas correctamente o agregue las palabras a un diccionario personalizado. Para obtener información sobre cómo usar los diccionarios personalizados, vea [CA1704: los identificadores deben estar escritos correctamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla. Palabras escritas correctamente reducen el tiempo necesario para aprender nuevas bibliotecas de software.

## <a name="related-rules"></a>Reglas relacionadas
 [CA1701: En las palabras compuestas de la cadena de recursos se deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

 [CA1704: Los identificadores deberían tener la ortografía correcta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

 [CA2204: Los literales deben estar escritos correctamente ](../code-quality/ca2204-literals-should-be-spelled-correctly.md)



