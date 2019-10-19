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
ms.openlocfilehash: 111f0b85a601d931ac17bde46f7170fa81e71815
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661396"
---
# <a name="ca1307-specify-stringcomparison"></a>CA1307: Especificar StringComparison
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SpecifyStringComparison|
|Identificador de comprobación|CA1307|
|Categoría|Microsoft. Globalization|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Una operación de comparación de cadenas utiliza una sobrecarga de método que no establece un parámetro <xref:System.StringComparison>.

## <a name="rule-description"></a>Descripción de la regla
 Muchas operaciones de cadena, más importantes los métodos <xref:System.String.Compare%2A> y <xref:System.String.Equals%2A>, proporcionan una sobrecarga que acepta un valor de enumeración <xref:System.StringComparison> como parámetro.

 Siempre que existe una sobrecarga que toma un parámetro <xref:System.StringComparison>, se debe usar en lugar de una sobrecarga que no tome este parámetro. Al establecer este parámetro explícitamente, el código suele ser más claro y más fácil de mantener.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambie los métodos de comparación de cadenas a las sobrecargas que aceptan la enumeración <xref:System.StringComparison> como un parámetro. Por ejemplo: cambie `String.Compare(str1, str2)` a `String.Compare(str1, str2, StringComparison.Ordinal)`.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla cuando la biblioteca o aplicación está pensada para un público local limitado y, por lo tanto, no se localizará.

## <a name="see-also"></a>Vea también
 [Advertencias de globalización](../code-quality/globalization-warnings.md) [CA1309: Use StringComparison ordinal](../code-quality/ca1309-use-ordinal-stringcomparison.md)
