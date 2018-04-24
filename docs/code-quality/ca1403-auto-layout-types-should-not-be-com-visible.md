---
title: 'CA1403: Los tipos de diseño automático no deben ser visibles para COM'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2559f5d281a9669d2d36419eaeccd5ad879ce926
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="ca1403-auto-layout-types-should-not-be-com-visible"></a>CA1403: Los tipos de diseño automático no deben ser visibles para COM
|||
|-|-|
|TypeName|AutoLayoutTypesShouldNotBeComVisible|
|Identificador de comprobación|CA1403|
|Categoría|Microsoft.Interoperability|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo de valor visible del modelo de objetos componentes (COM) se marca con la <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName> atributo establecido en <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=fullName>.

## <a name="rule-description"></a>Descripción de la regla
 <xref:System.Runtime.InteropServices.LayoutKind> tipos de diseño se administran por common language runtime. El diseño de estos tipos puede cambiar entre las versiones de .NET Framework, lo que interrumpirá a los clientes COM que esperan un diseño concreto. Tenga en cuenta que si el <xref:System.Runtime.InteropServices.StructLayoutAttribute> no se especifica el atributo, C#, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], y los compiladores de C++ especifican el <xref:System.Runtime.InteropServices.LayoutKind> diseño para los tipos de valor.

 A menos que marque lo contrario, todos los tipos no genéricos públicos son visibles para COM; todos los tipos no públicos y genéricos son invisibles para COM. Sin embargo, para reducir los falsos positivos, esta regla requiere que la visibilidad de COM del tipo que se establezca explícitamente; el ensamblado que lo contiene se debe marcar con el <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> establecido en `false` y el tipo se debe marcar con el <xref:System.Runtime.InteropServices.ComVisibleAttribute> establecido en `true`.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambie el valor de la <xref:System.Runtime.InteropServices.StructLayoutAttribute> atribuir a <xref:System.Runtime.InteropServices.LayoutKind> o <xref:System.Runtime.InteropServices.LayoutKind>, o hacer que el tipo no visible para COM.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un tipo que infringe la regla y un tipo que infringe la regla.

 [!code-csharp[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/CSharp/ca1403-auto-layout-types-should-not-be-com-visible_1.cs)]
 [!code-vb[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/VisualBasic/ca1403-auto-layout-types-should-not-be-com-visible_1.vb)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1408: No utilizar AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>Vea también
 [Habilitar tipos de .NET para la interoperación](/dotnet/framework/interop/qualifying-net-types-for-interoperation) [interoperar con código no administrado](/dotnet/framework/interop/index)