---
title: 'CA1406: Evite argumentos Int64 para clientes Visual Basic 6 | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
helpviewer_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
ms.assetid: d5d0d3fc-f105-43da-be5b-923ab023309c
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5947ce0bbcb19058cb32950e1e77cb3566b2ad2e
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591941"
---
# <a name="ca1406-avoid-int64-arguments-for-visual-basic-6-clients"></a>CA1406: Evite argumentos Int64 para clientes Visual Basic 6
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [CA1406: argumentos evitar Int64 para clientes Visual Basic 6](https://docs.microsoft.com/visualstudio/code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients).

|||
|-|-|
|TypeName|AvoidInt64ArgumentsForVB6Clients|
|Identificador de comprobación|CA1406|
|Categoría|Microsoft.Interoperability|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo marcado específicamente como visible para el modelo de objetos componentes (COM) declara un miembro que toma un <xref:System.Int64?displayProperty=fullName> argumento.

## <a name="rule-description"></a>Descripción de la regla
 Los clientes COM de Visual Basic 6 no pueden tener acceso a los enteros de 64 bits.

 De forma predeterminada, los siguientes son visibles para COM: ensamblados, tipos públicos, los miembros de instancia públicos en tipos públicos y todos los miembros de tipos de valor público. Sin embargo, para reducir los falsos positivos, esta regla requiere que la visibilidad de COM de tipo explícita; el ensamblado contenedor debe estar marcado con el <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> establecido en `false` y el tipo se debe marcar con el <xref:System.Runtime.InteropServices.ComVisibleAttribute> establecido en `true`.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla para un parámetro cuyo valor siempre se puede expresar como un entero de 32 bits, cambie el tipo de parámetro a <xref:System.Int32?displayProperty=fullName>. Si el valor del parámetro puede ser mayor que se puede expresar como un entero de 32 bits, cambie el tipo de parámetro a <xref:System.Decimal?displayProperty=fullName>. Tenga en cuenta que ambos <xref:System.Single?displayProperty=fullName> y <xref:System.Double?displayProperty=fullName> perder precisión en los intervalos superiores de la <xref:System.Int64> tipo de datos. Si el miembro no está pensado para ser visibles para COM, márquelo con el <xref:System.Runtime.InteropServices.ComVisibleAttribute> establecido en `false`.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si tiene la certeza de que los clientes COM de Visual Basic 6 no tendrá acceso a la del tipo.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un tipo que infringe la regla.

 [!code-csharp[FxCop.Interoperability.LongArgument#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LongArgument/cs/FxCop.Interoperability.LongArgument.cs#1)]
 [!code-vb[FxCop.Interoperability.LongArgument#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LongArgument/vb/FxCop.Interoperability.LongArgument.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1413: Evite campos no públicos en tipos de valor visibles para COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

 [CA1407: Evite miembros estáticos en tipos visibles para COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017: Marque los ensamblados con ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Vea también
 [Interoperar con código no administrado](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258) [tipo de datos Long](http://msdn.microsoft.com/library/b4770c34-1804-4f8c-b512-c10b0893e516)



