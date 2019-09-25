---
title: 'CA1403: Los tipos de diseño automático no deben ser visibles a través de COM'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AutoLayoutTypesShouldNotBeComVisible
- CA1403
helpviewer_keywords:
- CA1403
- AutoLayoutTypesShouldNotBeComVisible
ms.assetid: a7007714-f9b4-4730-94e0-67d3dc68991f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 4e590514247444d32d0d9a31b2bbc409434cf53c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234834"
---
# <a name="ca1403-auto-layout-types-should-not-be-com-visible"></a>CA1403: Los tipos de diseño automático no deben ser visibles a través de COM

|||
|-|-|
|TypeName|AutoLayoutTypesShouldNotBeComVisible|
|Identificador de comprobación|CA1403|
|Categoría|Microsoft.Interoperability|
|Cambio importante|Problemático|

## <a name="cause"></a>Motivo

Un tipo de valor visible del modelo de objetos componentes (com) se <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName> marca con el <xref:System.Runtime.InteropServices.LayoutKind.Auto?displayProperty=fullName>atributo establecido en.

## <a name="rule-description"></a>Descripción de la regla

<xref:System.Runtime.InteropServices.LayoutKind>los tipos de diseño se administran mediante el Common Language Runtime. El diseño de estos tipos puede cambiar entre versiones de .NET, lo que interrumpe los clientes COM que esperan un diseño específico. Si no <xref:System.Runtime.InteropServices.StructLayoutAttribute> se especifica el atributo, los C#compiladores, C++ Visual Basic y, especifican [LayoutKind. auto](<xref:System.Runtime.InteropServices.LayoutKind.Auto>) para los tipos de valor.

A menos que se indique lo contrario, todos los tipos públicos y no genéricos son visibles para COM, y todos los tipos no públicos y genéricos son invisibles para COM. Sin embargo, para reducir los falsos positivos, esta regla requiere que la visibilidad COM del tipo se indique explícitamente. El ensamblado contenedor debe marcarse con <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> el establecido `false` en y el tipo debe estar marcado con <xref:System.Runtime.InteropServices.ComVisibleAttribute> el establecido `true`en.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, cambie el valor del <xref:System.Runtime.InteropServices.StructLayoutAttribute> atributo a [LayoutKind. Explicit](<xref:System.Runtime.InteropServices.LayoutKind.Explicit>) o [LayoutKind. Sequential](<xref:System.Runtime.InteropServices.LayoutKind.Sequential>), o haga que el tipo sea invisible para com.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra un tipo que infringe la regla y un tipo que cumple la regla.

[!code-csharp[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/CSharp/ca1403-auto-layout-types-should-not-be-com-visible_1.cs)]
[!code-vb[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/VisualBasic/ca1403-auto-layout-types-should-not-be-com-visible_1.vb)]

## <a name="related-rules"></a>Reglas relacionadas

[CA1408: No usar AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>Vea también

- [Calificar tipos de .NET para la interoperación](/dotnet/framework/interop/qualifying-net-types-for-interoperation)
- [Interoperar con código no administrado](/dotnet/framework/interop/index)