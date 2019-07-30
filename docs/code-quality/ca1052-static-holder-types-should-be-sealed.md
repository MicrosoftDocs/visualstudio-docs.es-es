---
title: 'CA1052: Los tipos de titulares estáticos deben ser estáticos o NotInheritable'
ms.date: 07/25/2019
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
ms.openlocfilehash: 0a574f7f77277255acf2150c218c3f4db061e75c
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/29/2019
ms.locfileid: "68604767"
---
# <a name="ca1052-static-holder-types-should-be-static-or-notinheritable"></a>CA1052: Los tipos de titulares estáticos deben ser estáticos o NotInheritable

|||
|-|-|
|TypeName|StaticHolderTypesAnalyzer|
|Identificador de comprobación|CA1052|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa

Un tipo no abstracto solo contiene miembros estáticos (distintos de un posible constructor predeterminado) y no se ha declarado con el modificador [static](/dotnet/csharp/language-reference/keywords/static) o [Shared](/dotnet/visual-basic/language-reference/modifiers/shared) .

De forma predeterminada, esta regla solo examina los tipos visibles externamente, pero esto es [configurable](#configurability).

## <a name="rule-description"></a>Descripción de la regla

La regla CA1052 supone que un tipo que solo contiene miembros estáticos no está diseñado para ser heredado, porque el tipo no proporciona ninguna funcionalidad que se pueda invalidar en un tipo derivado. Un tipo que no está diseñado para ser heredado se debe marcar con `static` el modificador C# en para prohibir su uso como tipo base. Además, se debe quitar su constructor predeterminado. En Visual Basic, la clase se debe convertir en un [módulo](/dotnet/visual-basic/language-reference/statements/module-statement).

Esta regla no se activa para clases abstractas o clases que tienen una clase base. Sin embargo, la regla se activa para las clases que admiten una interfaz vacía.

> [!NOTE]
> En la implementación del analizador de FxCop de esta regla, también engloba la funcionalidad de [CA1053 de reglas](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md).

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, marque el tipo `static` como y quite el constructor predeterminadoC#() o conviértalo en un módulo (Visual Basic).

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

Suprima una advertencia de esta regla solo si el tipo está diseñado para ser heredado. La ausencia del `static` modificador sugiere que el tipo es útil como un tipo base.

## <a name="configurability"></a>Configurabilidad

Si está ejecutando esta regla desde los [analizadores de FxCop](install-fxcop-analyzers.md) (y no mediante el análisis de código estático), puede configurar en qué partes del código base ejecutar esta regla, según su accesibilidad. Por ejemplo, para especificar que la regla se debe ejecutar solo en la superficie de API no pública, agregue el siguiente par clave-valor a un archivo EditorConfig en el proyecto:

```ini
dotnet_code_quality.ca1052.api_surface = private, internal
```

Puede configurar esta opción solo para esta regla, para todas las reglas o para todas las reglas de esta categoría (diseño). Para obtener más información, vea [configurar analizadores de FxCop](configure-fxcop-analyzers.md).

## <a name="example-of-a-violation"></a>Ejemplo de una infracción

En el ejemplo siguiente se muestra un tipo que infringe la regla:

[!code-csharp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_1.cs)]
[!code-vb[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/VisualBasic/ca1052-static-holder-types-should-be-sealed_1.vb)]
[!code-cpp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CPP/ca1052-static-holder-types-should-be-sealed_1.cpp)]

## <a name="fix-with-the-static-modifier"></a>Corrección con el modificador static

En el ejemplo siguiente se muestra cómo corregir una infracción de esta regla marcando el tipo `static` con el modificador en: C#

```csharp
public static class StaticMembers
{
    public static int SomeProperty { get; set; }
    public static void SomeMethod() { }
}
```