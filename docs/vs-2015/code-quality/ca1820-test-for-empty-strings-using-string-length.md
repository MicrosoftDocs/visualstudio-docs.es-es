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
ms.openlocfilehash: 296eb6407e3ce63b0eb28ff86c215c12ec724ce9
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545319"
---
# <a name="ca1820-test-for-empty-strings-using-string-length"></a>CA1820: Comprobar si las cadenas están vacías mediante la longitud de cadena
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Valor|
|-|-|
|TypeName|TestForEmptyStringsUsingStringLength|
|Identificador de comprobación|CA1820|
|Categoría|Microsoft. performance|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Causa
 Una cadena se compara con la cadena vacía mediante <xref:System.Object.Equals%2A?displayProperty=fullName> .

## <a name="rule-description"></a>Descripción de la regla
 La comparación de cadenas mediante la <xref:System.String.Length%2A?displayProperty=fullName> propiedad o el <xref:System.String.IsNullOrEmpty%2A?displayProperty=fullName> método es significativamente más rápida que el uso de <xref:System.Object.Equals%2A> . Esto se debe <xref:System.Object.Equals%2A> a que ejecuta mucho más instrucciones MSIL que <xref:System.String.IsNullOrEmpty%2A> o el número de instrucciones ejecutadas para recuperar el valor de propiedad y compararlo <xref:System.String.Length%2A> con cero.

 Debe tener en cuenta que <xref:System.Object.Equals%2A> y <xref:System.String.Length%2A> = = 0 se comportan de manera diferente para las cadenas nulas. Si intenta obtener el valor de la <xref:System.String.Length%2A> propiedad en una cadena nula, el Common Language Runtime produce una excepción <xref:System.NullReferenceException?displayProperty=fullName> . Si realiza una comparación entre una cadena nula y la cadena vacía, el Common Language Runtime no inicia una excepción; la comparación devuelve `false` . La comprobación de NULL no afecta significativamente al rendimiento relativo de estos dos enfoques. Cuando el destino es [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] , use el <xref:System.String.IsNullOrEmpty%2A> método. De lo contrario, use la <xref:System.String.Length%2A> comparación = = siempre que sea posible.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambie la comparación para usar la <xref:System.String.Length%2A> propiedad y probar la cadena nula. Si el destino es [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] , use el <xref:System.String.IsNullOrEmpty%2A> método.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si el rendimiento no es un problema.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestran las distintas técnicas que se usan para buscar una cadena vacía.

 [!code-csharp[FxCop.Performance.StringTest#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.StringTest/cs/FxCop.Performance.StringTest.cs#1)]
