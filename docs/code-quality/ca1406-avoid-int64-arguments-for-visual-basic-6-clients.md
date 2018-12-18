---
title: 'CA1406: Evite argumentos Int64 para clientes Visual Basic 6'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
helpviewer_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
ms.assetid: d5d0d3fc-f105-43da-be5b-923ab023309c
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: f6eeda13b8dc7a05622613f719a6b2a85b61835a
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/13/2018
ms.locfileid: "45546881"
---
# <a name="ca1406-avoid-int64-arguments-for-visual-basic-6-clients"></a>CA1406: Evite argumentos Int64 para clientes Visual Basic 6

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

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si tiene la certeza de que los clientes COM de Visual Basic 6 no tendrá acceso a la del tipo.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un tipo que infringe la regla.

 [!code-csharp[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/CSharp/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.cs)]
 [!code-vb[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/VisualBasic/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.vb)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1413: Evite campos no públicos en tipos de valor visibles para COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

 [CA1407: Evite miembros estáticos en tipos visibles para COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017: Marque los ensamblados con ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Vea también

- [Interoperating with Unmanaged Code](/dotnet/framework/interop/index) (Interoperar con código no administrado)
- [Long (tipo de datos)](/dotnet/visual-basic/language-reference/data-types/long-data-type)