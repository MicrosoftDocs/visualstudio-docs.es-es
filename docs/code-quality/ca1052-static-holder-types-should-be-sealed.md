---
title: 'CA1052: Los tipos titulares estáticos deben estar sellados'
ms.date: 11/09/2018
ms.topic: reference
f1_keywords:
- StaticHolderTypesShouldBeSealed
- CA1052
helpviewer_keywords:
- CA1052
- StaticHolderTypesShouldBeSealed
ms.assetid: 51a3165d-781e-4a55-aa0d-ea25fee7d4f2
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 36bd459f2a9f7300328aadd3509530f4802e71cd
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55922458"
---
# <a name="ca1052-static-holder-types-should-be-sealed"></a>CA1052: Los tipos titulares estáticos deben estar sellados

|||
|-|-|
|TypeName|StaticHolderTypesShouldBeSealed|
|Identificador de comprobación|CA1052|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo

Un público o protegido, no abstracta tipo contiene sólo miembros estáticos y no se ha declarado con el [sealed](/dotnet/csharp/language-reference/keywords/sealed) ([NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)) modificador.

## <a name="rule-description"></a>Descripción de la regla

CA1052 regla supone que un tipo que contiene a sólo miembros estáticos no está diseñado para heredarse, porque el tipo no proporciona ninguna funcionalidad que se puede invalidar en un tipo derivado. Un tipo que no está diseñado para heredarse debería marcarse con el `sealed` o `NotInheritable` modificador para prohibir su uso como un tipo base. Esta regla se desencadena para las clases abstractas.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, marque el tipo como `sealed` o `NotInheritable`. Si tiene como destino .NET Framework 2.0 o versiones posteriores, un mejor enfoque es marcar el tipo como `static` o `Shared`. De esta manera, no debe declarar un constructor privado para evitar que la clase que se está creando.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

Suprima una advertencia de esta regla sólo si el tipo está diseñado para heredarse. La ausencia de la `sealed` o `NotInheritable` modificador sugiere que el tipo es útil como tipo base.

## <a name="example-of-a-violation"></a>Ejemplo de una infracción

El ejemplo siguiente muestra un tipo que infringe la regla.

[!code-csharp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_1.cs)]
[!code-vb[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/VisualBasic/ca1052-static-holder-types-should-be-sealed_1.vb)]
[!code-cpp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CPP/ca1052-static-holder-types-should-be-sealed_1.cpp)]

## <a name="fix-with-the-static-modifier"></a>Corregir con el modificador "static"

El ejemplo siguiente muestra cómo corregir una infracción de esta regla, marque el tipo con el `static` modificador en C#.

[!code-csharp[FxCop.Design.StaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_2.cs)]

## <a name="related-rules"></a>Reglas relacionadas

[CA1053: Los tipos titulares estáticos no deben tener constructores](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)