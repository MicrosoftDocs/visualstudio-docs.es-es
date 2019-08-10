---
title: 'CA1406: Evitar los argumentos Int64 en clientes Visual Basic 6'
ms.date: 11/04/2016
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
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 4dfcc612e931756b0e3d817556c9b37844bc3cfd
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922035"
---
# <a name="ca1406-avoid-int64-arguments-for-visual-basic-6-clients"></a>CA1406: Evitar los argumentos Int64 en clientes Visual Basic 6

|||
|-|-|
|TypeName|AvoidInt64ArgumentsForVB6Clients|
|Identificador de comprobación|CA1406|
|Categoría|Microsoft.Interoperability|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
Un tipo que está marcado específicamente como visible para el modelo de objetos componentes (com) declara un miembro que toma <xref:System.Int64?displayProperty=fullName> un argumento.

## <a name="rule-description"></a>Descripción de la regla
Los clientes COM de Visual Basic 6 no pueden tener acceso a los enteros de 64 bits.

De forma predeterminada, los siguientes elementos son visibles para COM: ensamblados, tipos públicos, miembros de instancia pública en tipos públicos y todos los miembros de tipos de valor públicos. Sin embargo, para reducir los falsos positivos, esta regla requiere que se indique explícitamente la visibilidad COM del tipo; el ensamblado contenedor debe marcarse con <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> el establecido `false` en y el tipo debe estar marcado con <xref:System.Runtime.InteropServices.ComVisibleAttribute> el establecido `true`en.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla para un parámetro cuyo valor siempre se puede expresar como un entero de 32 bits, cambie el tipo de <xref:System.Int32?displayProperty=fullName>parámetro a. Si el valor del parámetro puede ser mayor que se puede expresar como un entero de 32 bits, cambie el tipo de parámetro a <xref:System.Decimal?displayProperty=fullName>. Tenga en cuenta <xref:System.Single?displayProperty=fullName> que <xref:System.Double?displayProperty=fullName> y pierden precisión en <xref:System.Int64> los intervalos superiores del tipo de datos. Si el miembro no está diseñado para ser visible para com, márquelo con el <xref:System.Runtime.InteropServices.ComVisibleAttribute> establecido en. `false`

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
Es seguro suprimir una advertencia de esta regla si está seguro de que Visual Basic 6 clientes COM no tendrán acceso al tipo.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra un tipo que infringe la regla.

[!code-csharp[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/CSharp/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.cs)]
[!code-vb[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/VisualBasic/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.vb)]

## <a name="related-rules"></a>Reglas relacionadas
[CA1413: Evitar campos no públicos en tipos de valor visibles para COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

[CA1407: Evitar miembros estáticos en tipos visibles para COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

[CA1017: Marcar ensamblados con ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Vea también

- [Interoperating with Unmanaged Code](/dotnet/framework/interop/index) (Interoperar con código no administrado)
- [Long (tipo de datos)](/dotnet/visual-basic/language-reference/data-types/long-data-type)