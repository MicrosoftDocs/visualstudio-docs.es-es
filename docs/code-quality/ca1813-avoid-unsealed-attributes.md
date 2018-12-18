---
title: 'CA1813: Evitar atributos no sellados'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 45804f08ea25ab8582d28632baf07abea24e0406
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/01/2018
ms.locfileid: "47859489"
---
# <a name="ca1813-avoid-unsealed-attributes"></a>CA1813: Evitar atributos no sellados

|||
|-|-|
|TypeName|AvoidUnsealedAttributes|
|Identificador de comprobación|CA1813|
|Categoría|Microsoft.Performance|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo

Un tipo público hereda de <xref:System.Attribute?displayProperty=fullName>, no es abstracta y no está sellado (`NotInheritable` en Visual Basic).

## <a name="rule-description"></a>Descripción de la regla

La biblioteca de clases de .NET Framework proporciona métodos para recuperar los atributos personalizados. De forma predeterminada, estos métodos buscan la jerarquía de herencia de atributo. Por ejemplo, <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=fullName> busca el tipo de atributo especificado o cualquier tipo de atributo que extiende el tipo de atributo especificado. Sellar el atributo elimina la búsqueda a través de la jerarquía de herencia y puede mejorar el rendimiento.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, selle el tipo de atributo o establecerlo como abstracto.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

Es seguro suprimir una advertencia de esta regla. Suprimir solo si está definiendo una jerarquía de atributo y no se puede sellar el atributo o establecerlo como abstracto.

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra un atributo personalizado que cumple esta regla.

[!code-csharp[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/CSharp/ca1813-avoid-unsealed-attributes_1.cs)]
[!code-vb[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/VisualBasic/ca1813-avoid-unsealed-attributes_1.vb)]

## <a name="related-rules"></a>Reglas relacionadas

- [CA1019: Definir descriptores de acceso para los argumentos de atributo](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)
- [CA1018: Marcar atributos con AttributeUsageAttribute](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)

## <a name="see-also"></a>Vea también

- [Atributos](/dotnet/standard/design-guidelines/attributes)