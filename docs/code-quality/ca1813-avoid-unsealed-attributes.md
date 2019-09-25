---
title: 'CA1813: Evitar los atributos no sellados'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1813
- AvoidUnsealedAttributes
helpviewer_keywords:
- CA1813
- AvoidUnsealedAttributes
ms.assetid: f5e31b4c-9f8b-49e1-a2a8-bb5f1140729a
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 12371c34c846991a0ec41f5e9d9588c5bde8e4d6
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233599"
---
# <a name="ca1813-avoid-unsealed-attributes"></a>CA1813: Evitar los atributos no sellados

|||
|-|-|
|TypeName|AvoidUnsealedAttributes|
|Identificador de comprobación|CA1813|
|Categoría|Microsoft.Performance|
|Cambio importante|Problemático|

## <a name="cause"></a>Motivo

Un tipo público hereda de <xref:System.Attribute?displayProperty=fullName>, no es abstracto y no está sellado (`NotInheritable` en Visual Basic).

## <a name="rule-description"></a>Descripción de la regla

.NET proporciona métodos para recuperar atributos personalizados. De forma predeterminada, estos métodos buscan la jerarquía de herencia de atributo. Por ejemplo, <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=fullName> busca el tipo de atributo especificado o cualquier tipo de atributo que extienda el tipo de atributo especificado. Al sellar el atributo, se elimina la búsqueda a través de la jerarquía de herencia y puede mejorar el rendimiento.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, selle el tipo de atributo o haga que sea abstracto.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

Es seguro suprimir una advertencia de esta regla. Suprima solo si está definiendo una jerarquía de atributo y no puede sellar el atributo ni hacer que sea abstracto.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra un atributo personalizado que cumple esta regla.

[!code-csharp[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/CSharp/ca1813-avoid-unsealed-attributes_1.cs)]
[!code-vb[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/VisualBasic/ca1813-avoid-unsealed-attributes_1.vb)]

## <a name="related-rules"></a>Reglas relacionadas

- [CA1019: Definir los descriptores de acceso para los argumentos de atributo](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)
- [CA1018: Marcar atributos con AttributeUsageAttribute](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)

## <a name="see-also"></a>Vea también

- [Atributos](/dotnet/standard/design-guidelines/attributes)