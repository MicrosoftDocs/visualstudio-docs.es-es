---
title: 'CA1405: Los tipos base de tipos visibles a través de COM deben ser visibles a través de COM'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
helpviewer_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
ms.assetid: a762ea2f-5285-4f73-bfb9-9eb10aea4290
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8e4e5c4ed258bcc88fedbb6d015fed576d326a0f
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234957"
---
# <a name="ca1405-com-visible-type-base-types-should-be-com-visible"></a>CA1405: Los tipos base de tipos visibles a través de COM deben ser visibles a través de COM

|||
|-|-|
|TypeName|ComVisibleTypeBaseTypesShouldBeComVisible|
|Identificador de comprobación|CA1405|
|Categoría|Microsoft.Interoperability|
|Cambio importante|DependsOnFix|

## <a name="cause"></a>Motivo
Un tipo visible del modelo de objetos componentes (COM) deriva de un tipo que no es visible para COM.

## <a name="rule-description"></a>Descripción de la regla
Cuando un tipo visible para COM agrega miembros en una nueva versión, debe cumplir instrucciones estrictas para evitar la interrupción de los clientes COM que se enlazan a la versión actual. Un tipo que no es visible para COM presupone que no tiene que seguir estas reglas de control de versiones COM cuando agrega nuevos miembros. Sin embargo, si un tipo visible com se deriva del tipo com invisible y expone una interfaz de clase de <xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName> o <xref:System.Runtime.InteropServices.ClassInterfaceType> (valor predeterminado), todos los miembros públicos del tipo base (a menos que se marquen específicamente como com invisible, que serían redundantes) se exponen a COM. Si el tipo base agrega nuevos miembros en una versión posterior, los clientes COM que se enlazan a la interfaz de clase del tipo derivado podrían interrumpirse. Los tipos visibles para COM solo se deben derivar de tipos visibles para COM para reducir la posibilidad de interrumpir los clientes COM.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, haga que los tipos base COM sean visibles o el tipo derivado de COM invisible.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra un tipo que infringe la regla.

[!code-vb[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1405-com-visible-type-base-types-should-be-com-visible_1.vb)]
[!code-csharp[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/CSharp/ca1405-com-visible-type-base-types-should-be-com-visible_1.cs)]

## <a name="see-also"></a>Vea también

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute?displayProperty=fullName>
- [Interoperating with Unmanaged Code](/dotnet/framework/interop/index) (Interoperar con código no administrado)