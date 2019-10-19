---
title: 'CA1406: Evite argumentos Int64 para clientes Visual Basic 6 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
helpviewer_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
ms.assetid: d5d0d3fc-f105-43da-be5b-923ab023309c
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c20ea7bd7bba6f221395c7e2c21d6c1dcc241fb4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661296"
---
# <a name="ca1406-avoid-int64-arguments-for-visual-basic-6-clients"></a>CA1406: Evite argumentos Int64 para clientes Visual Basic 6
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidInt64ArgumentsForVB6Clients|
|Identificador de comprobación|CA1406|
|Categoría|Microsoft. Interoperability|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo que está marcado específicamente como visible para el modelo de objetos componentes (COM) declara un miembro que toma un argumento <xref:System.Int64?displayProperty=fullName>.

## <a name="rule-description"></a>Descripción de la regla
 Los clientes COM de Visual Basic 6 no pueden tener acceso a enteros de 64 bits.

 De forma predeterminada, los siguientes elementos son visibles para COM: ensamblados, tipos públicos, miembros de instancia pública en tipos públicos y todos los miembros de tipos de valor públicos. Sin embargo, para reducir los falsos positivos, esta regla requiere que se indique explícitamente la visibilidad COM del tipo; el ensamblado contenedor debe marcarse con la <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> establecida en `false` y el tipo debe estar marcado con el <xref:System.Runtime.InteropServices.ComVisibleAttribute> establecido en `true`.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla para un parámetro cuyo valor siempre se puede expresar como una integral de 32 bits, cambie el tipo de parámetro a <xref:System.Int32?displayProperty=fullName>. Si el valor del parámetro puede ser mayor que se puede expresar como un entero de 32 bits, cambie el tipo de parámetro a <xref:System.Decimal?displayProperty=fullName>. Tenga en cuenta que tanto <xref:System.Single?displayProperty=fullName> como <xref:System.Double?displayProperty=fullName> pierden precisión en los intervalos superiores del tipo de datos <xref:System.Int64>. Si el miembro no está diseñado para ser visible para COM, márquelo con la <xref:System.Runtime.InteropServices.ComVisibleAttribute> establecida en `false`.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si está seguro de que Visual Basic 6 clientes COM no tendrán acceso al tipo.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un tipo que infringe la regla.

 [!code-csharp[FxCop.Interoperability.LongArgument#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LongArgument/cs/FxCop.Interoperability.LongArgument.cs#1)]
 [!code-vb[FxCop.Interoperability.LongArgument#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LongArgument/vb/FxCop.Interoperability.LongArgument.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1413: Evite campos no públicos en tipos de valor visibles para COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

 [CA1407: Evite miembros estáticos en tipos visibles para COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017: Marque los ensamblados con ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Vea también
 Interoperar con el [tipo de datos Long](https://msdn.microsoft.com/library/b4770c34-1804-4f8c-b512-c10b0893e516) [de código no administrado](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
