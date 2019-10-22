---
title: 'CA1820: prueba de cadenas vacías con longitud de cadena | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
helpviewer_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
ms.assetid: da1e70c8-b1dc-46b9-8b8f-4e6e48339681
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6711dac907de2777cf892b20269fec7e99d3bd6f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657503"
---
# <a name="ca1820-test-for-empty-strings-using-string-length"></a>CA1820: Comprobar si las cadenas están vacías mediante la longitud de cadena
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TestForEmptyStringsUsingStringLength|
|Identificador de comprobación|CA1820|
|Categoría|Microsoft. performance|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Una cadena se compara con la cadena vacía mediante <xref:System.Object.Equals%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Descripción de la regla
 Comparar cadenas mediante la propiedad <xref:System.String.Length%2A?displayProperty=fullName> o el método <xref:System.String.IsNullOrEmpty%2A?displayProperty=fullName> es significativamente más rápido que usar <xref:System.Object.Equals%2A>. Esto se debe a que <xref:System.Object.Equals%2A> ejecuta muchas más instrucciones de MSIL que <xref:System.String.IsNullOrEmpty%2A> o el número de instrucciones ejecutadas para recuperar el valor de la propiedad <xref:System.String.Length%2A> y compararlo con cero.

 Tenga en cuenta que <xref:System.Object.Equals%2A> y <xref:System.String.Length%2A> = = 0 se comportan de manera diferente para las cadenas nulas. Si intenta obtener el valor de la propiedad <xref:System.String.Length%2A> en una cadena nula, el Common Language Runtime inicia una <xref:System.NullReferenceException?displayProperty=fullName>. Si realiza una comparación entre una cadena nula y la cadena vacía, el Common Language Runtime no inicia una excepción; la comparación devuelve `false`. La comprobación de NULL no afecta significativamente al rendimiento relativo de estos dos enfoques. Cuando el destino sea [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)], utilice el método <xref:System.String.IsNullOrEmpty%2A>. De lo contrario, use la comparación <xref:System.String.Length%2A> = = siempre que sea posible.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambie la comparación para usar la propiedad <xref:System.String.Length%2A> y probar la cadena null. Si el destino es [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)], utilice el método <xref:System.String.IsNullOrEmpty%2A>.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si el rendimiento no es un problema.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestran las distintas técnicas que se usan para buscar una cadena vacía.

 [!code-csharp[FxCop.Performance.StringTest#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.StringTest/cs/FxCop.Performance.StringTest.cs#1)]
