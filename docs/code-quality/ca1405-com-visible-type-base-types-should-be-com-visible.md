---
title: 'CA1405: Los tipos base de tipos visibles a través de COM deben ser visibles a través de COM'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: c0221231956c565eb2ce3792d0c88864b0e13e65
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53839328"
---
# <a name="ca1405-com-visible-type-base-types-should-be-com-visible"></a>CA1405: Los tipos base de tipos visibles a través de COM deben ser visibles a través de COM

|||
|-|-|
|TypeName|ComVisibleTypeBaseTypesShouldBeComVisible|
|Identificador de comprobación|CA1405|
|Categoría|Microsoft.Interoperability|
|Cambio problemático|Depende de la corrección|

## <a name="cause"></a>Motivo
 Un tipo visible del modelo de objetos componentes (COM) se deriva de un tipo que no es visible para COM.

## <a name="rule-description"></a>Descripción de la regla
 Cuando un tipo visible COM agrega miembros en una nueva versión, debe cumplir las instrucciones estrictas para evitar que los clientes COM que se enlazan a la versión actual. Un tipo que no es visible para COM se da por supuesto que no tiene que seguir estas reglas de control de versiones de COM cuando agrega nuevos miembros. Sin embargo, si un visibles para COM tipo deriva del tipo visible COM y expone una interfaz de clase de <xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName> o <xref:System.Runtime.InteropServices.ClassInterfaceType> (valor predeterminado), todos los miembros públicos del tipo base (a menos que se marcado específicamente como COM invisibles, que sería redundante) se expone a COM. Si el tipo base agrega a nuevos miembros en una versión posterior, todos los clientes COM que se enlazan a la interfaz de clase del tipo derivado que se interrumpa. Los tipos visibles COM deben derivar solo de los tipos visibles COM para reducir la posibilidad de que los clientes COM.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, hacer que los tipos base visibles para COM o el tipo derivado COM sea invisible.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un tipo que infringe la regla.

 [!code-vb[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1405-com-visible-type-base-types-should-be-com-visible_1.vb)]
 [!code-csharp[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/CSharp/ca1405-com-visible-type-base-types-should-be-com-visible_1.cs)]

## <a name="see-also"></a>Vea también

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute?displayProperty=fullName>
- [Interoperating with Unmanaged Code](/dotnet/framework/interop/index) (Interoperar con código no administrado)