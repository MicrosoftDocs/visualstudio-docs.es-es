---
title: 'CA1307: especificar StringComparison | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1307
- SpecifyStringComparison
helpviewer_keywords:
- CA1307
- SpecifyStringComparison
ms.assetid: 9b0d5e71-1683-4a0d-bc4a-68b2fbd8af71
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 033d8f0e22ec040ffb10821993a5a9c647ee401e
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85538923"
---
# <a name="ca1307-specify-stringcomparison"></a>CA1307: Especificar StringComparison
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|SpecifyStringComparison|
|Identificador de comprobación|CA1307|
|Category|Microsoft. Globalization|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Causa
 Una operación de comparación de cadenas utiliza una sobrecarga de método que no establece un <xref:System.StringComparison> parámetro.

## <a name="rule-description"></a>Descripción de la regla
 Muchas operaciones de cadena, más importantes <xref:System.String.Compare%2A> los <xref:System.String.Equals%2A> métodos y, proporcionan una sobrecarga que acepta un <xref:System.StringComparison> valor de enumeración como parámetro.

 Siempre que existe una sobrecarga que toma un <xref:System.StringComparison> parámetro, se debe usar en lugar de una sobrecarga que no tome este parámetro. Al establecer este parámetro explícitamente, el código suele ser más claro y más fácil de mantener.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambie los métodos de comparación de cadenas a las sobrecargas que aceptan la <xref:System.StringComparison> enumeración como parámetro. Por ejemplo: cambie `String.Compare(str1, str2)` a `String.Compare(str1, str2, StringComparison.Ordinal)` .

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla cuando la biblioteca o aplicación está pensada para un público local limitado y, por lo tanto, no se localizará.

## <a name="see-also"></a>Consulte también
 [Advertencias de globalización](../code-quality/globalization-warnings.md) [CA1309: Use StringComparison ordinal](../code-quality/ca1309-use-ordinal-stringcomparison.md)
