---
title: 'CA1801: Revisar parámetros sin utilizar'
ms.date: 06/24/2019
ms.topic: reference
f1_keywords:
- AvoidUnusedParameters
- CA1801
- ReviewUnusedParameters
helpviewer_keywords:
- CA1801
- ReviewUnusedParameters
ms.assetid: 5d73545c-e153-4b7c-a7b2-be6bf5aca5be
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a73ce207d8efb0c6309ba52648c7231f89bc7984
ms.sourcegitcommit: 0f44ec8ba0263056ad04d2d0dc904ad4206ce8fc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2019
ms.locfileid: "70766042"
---
# <a name="ca1801-review-unused-parameters"></a>CA1801: Revisar parámetros sin utilizar

|||
|-|-|
|TypeName|ReviewUnusedParameters|
|Identificador de comprobación|CA1801|
|Categoría|Microsoft.Usage|
|Cambio problemático|No problemático: Si el miembro no es visible fuera del ensamblado, independientemente del cambio que realice.<br /><br /> No problemático: Si cambia el miembro para usar el parámetro dentro de su cuerpo.<br /><br /> Problemático: Si quita el parámetro y es visible fuera del ensamblado.|

## <a name="cause"></a>Causa

Una signatura de método incluye un parámetro que no se usa en el cuerpo del método.

Esta regla no examina los siguientes tipos de métodos:

- Métodos a los que hace referencia un delegado.

- Métodos usados como controladores de eventos.

- Métodos declarados `abstract` con`MustOverride` el modificador (en Visual Basic).

- Métodos declarados `virtual` con`Overridable` el modificador (en Visual Basic).

- Métodos declarados `override` con`Overrides` el modificador (en Visual Basic).

- Métodos declarados `extern` con`Declare` el modificador (instrucción in Visual Basic).

Si está utilizando [analizadores de FxCop](install-fxcop-analyzers.md), esta regla no marca los parámetros que se denominan con el símbolo de [descarte](/dotnet/csharp/discards) , `_`por `_1`ejemplo, `_2`, y. Esto reduce el ruido de advertencia en los parámetros que son necesarios para los requisitos de firma, por ejemplo, un método que se usa como delegado, un parámetro con atributos especiales o un parámetro cuyo valor es implícitamente accesible en tiempo de ejecución en un marco de trabajo, pero no se hace referencia a él en codifica.

## <a name="rule-description"></a>Descripción de la regla

Revise los parámetros de los métodos no virtuales que no se usan en el cuerpo del método para asegurarse de que no existe ninguna incorrección en torno al error de acceso. Los parámetros sin usar incurren en costos de mantenimiento y rendimiento.

A veces, una infracción de esta regla puede apuntar a un error de implementación en el método. Por ejemplo, el parámetro se debería haber utilizado en el cuerpo del método. Suprima las advertencias de esta regla si el parámetro debe existir debido a la compatibilidad con versiones anteriores.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, quite el parámetro sin usar (un cambio importante) o use el parámetro en el cuerpo del método (un cambio no problemático).

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

Es seguro suprimir una advertencia de esta regla:

- En código enviado previamente para el que la corrección sería un cambio importante.

- Para el `this` parámetro de un método de extensión personalizado <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=nameWithType>para. Las funciones de la <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> clase son estáticas, por lo que no es necesario tener `this` acceso al parámetro en el cuerpo del método.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestran dos métodos. Un método infringe la regla y el otro método cumple la regla.

[!code-csharp[FxCop.Usage.ReviewUnusedParameters#1](../code-quality/codesnippet/CSharp/ca1801-review-unused-parameters_1.cs)]

## <a name="related-rules"></a>Reglas relacionadas

[CA1811: Evitar código privado no llamado](../code-quality/ca1811-avoid-uncalled-private-code.md)

[CA1812: Evitar clases internas sin instancias](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

[CA1804: Quitar variables locales no usadas](../code-quality/ca1804-remove-unused-locals.md)
