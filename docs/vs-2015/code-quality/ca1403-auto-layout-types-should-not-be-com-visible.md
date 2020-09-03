---
title: 'CA1403: los tipos de diseño automático no deben ser visibles para COM | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AutoLayoutTypesShouldNotBeComVisible
- CA1403
helpviewer_keywords:
- CA1403
- AutoLayoutTypesShouldNotBeComVisible
ms.assetid: a7007714-f9b4-4730-94e0-67d3dc68991f
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1752efb5be1828f62703e1fe1a1130b37ff80503
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534932"
---
# <a name="ca1403-auto-layout-types-should-not-be-com-visible"></a>CA1403: Los tipos de diseño automático no deben ser visibles a través de COM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|AutoLayoutTypesShouldNotBeComVisible|
|Identificador de comprobación|CA1403|
|Category|Microsoft. Interoperability|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
 Un tipo de valor visible del modelo de objetos componentes (COM) se marca con el <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName> atributo establecido en <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=fullName> .

## <a name="rule-description"></a>Descripción de la regla
 <xref:System.Runtime.InteropServices.LayoutKind> los tipos de diseño se administran mediante el Common Language Runtime. El diseño de estos tipos puede cambiar entre las versiones del .NET Framework, lo que interrumpirá a los clientes COM que esperan un diseño específico. Tenga en cuenta que si <xref:System.Runtime.InteropServices.StructLayoutAttribute> no se especifica el atributo, los [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] compiladores de C++, y de C# especifican el <xref:System.Runtime.InteropServices.LayoutKind> diseño para los tipos de valor.

 A menos que se marque lo contrario, todos los tipos públicos no genéricos son visibles para COM; todos los tipos no públicos y genéricos son invisibles para COM. Sin embargo, para reducir los falsos positivos, esta regla requiere que se indique explícitamente la visibilidad COM del tipo; el ensamblado contenedor debe marcarse con el <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> establecido en `false` y el tipo debe estar marcado con el <xref:System.Runtime.InteropServices.ComVisibleAttribute> establecido en `true` .

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambie el valor del <xref:System.Runtime.InteropServices.StructLayoutAttribute> atributo a <xref:System.Runtime.InteropServices.LayoutKind> o o <xref:System.Runtime.InteropServices.LayoutKind> haga que el tipo sea invisible para com.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un tipo que infringe la regla y un tipo que cumple la regla.

 [!code-csharp[FxCop.Interoperability.AutoLayout#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoLayout/cs/FxCop.Interoperability.AutoLayout.cs#1)]
 [!code-vb[FxCop.Interoperability.AutoLayout#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoLayout/vb/FxCop.Interoperability.AutoLayout.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1408: No utilizar AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>Consulte también
 [Introducción a la interfaz de clase para la](https://msdn.microsoft.com/733c0dd2-12e5-46e6-8de1-39d5b25df024) [certificación de tipos de .net para](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd) la [interoperabilidad con código no administrado](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
