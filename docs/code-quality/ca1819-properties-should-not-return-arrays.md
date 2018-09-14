---
title: 'CA1819: Las propiedades no deberían devolver matrices'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PropertiesShouldNotReturnArrays
- CA1819
helpviewer_keywords:
- PropertiesShouldNotReturnArrays
- CA1819
ms.assetid: 85fcf312-57f8-438a-8b10-34441fe0bdeb
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 68f64d37a7616f095a86452353edc498d2d27f28
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/13/2018
ms.locfileid: "45549422"
---
# <a name="ca1819-properties-should-not-return-arrays"></a>CA1819: Las propiedades no deberían devolver matrices

|||
|-|-|
|TypeName|PropertiesShouldNotReturnArrays|
|Identificador de comprobación|CA1819|
|Categoría|Microsoft.Performance|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Una propiedad pública o protegida en un tipo público devuelve una matriz.

## <a name="rule-description"></a>Descripción de la regla
 Matrices devueltas por las propiedades no están protegidos contra escritura, incluso si la propiedad es de solo lectura. Para mantener la matriz inviolable, la propiedad debe devolver una copia de la matriz. Por lo general, los usuarios no entienden las implicaciones de rendimiento adversas que se originan al llamar a este tipo de propiedad. En concreto, puede usar la propiedad como una propiedad indizada.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, que la propiedad de un método o cambie la propiedad para devolver una colección.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 Los atributos pueden contener propiedades que devuelven matrices, pero no pueden contener propiedades que devuelven colecciones. Puede suprimir una advertencia que se genera para una propiedad de un atributo que se deriva el <xref:System.Attribute> clase. En caso contrario, no suprima una advertencia de esta regla.

## <a name="example-violation"></a>Infracción de ejemplo

### <a name="description"></a>Descripción
 El ejemplo siguiente muestra una propiedad que infringe esta regla.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_1.cs)]
 [!code-vb[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_1.vb)]

### <a name="comments"></a>Comentarios
 Para corregir una infracción de esta regla, que la propiedad de un método o cambie la propiedad para devolver una colección en lugar de una matriz.

## <a name="change-the-property-to-a-method-example"></a>Cambie la propiedad a un ejemplo del método

### <a name="description"></a>Descripción
 El ejemplo siguiente corrige la infracción cambiando la propiedad a un método.

### <a name="code"></a>Código
 [!code-vb[FxCop.Performance.PropertyArrayFixedMethod#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_2.vb)]
 [!code-csharp[FxCop.Performance.PropertyArrayFixedMethod#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_2.cs)]

## <a name="return-a-collection-example"></a>Devolver un ejemplo de la colección

### <a name="description"></a>Descripción
 En el ejemplo siguiente se corrige la infracción cambiando la propiedad para devolver una

 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Performance.PropertyArrayFixedCollection#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_3.cs)]
 [!code-vb[FxCop.Performance.PropertyArrayFixedCollection#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_3.vb)]

## <a name="allowing-users-to-modify-a-property"></a>Lo que permite a los usuarios modificar una propiedad

### <a name="description"></a>Descripción
 Es posible que desee permitir que el consumidor de la clase modificar una propiedad. El ejemplo siguiente muestra una propiedad de lectura/escritura que infringe esta regla.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Performance.PropertyModifyViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_4.cs)]
 [!code-vb[FxCop.Performance.PropertyModifyViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_4.vb)]

### <a name="comments"></a>Comentarios
 En el ejemplo siguiente se corrige la infracción cambiando la propiedad para devolver un <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>.

### <a name="code"></a>Código
 [!code-vb[FxCop.Performance.PropertyModifyFixed#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_5.vb)]
 [!code-csharp[FxCop.Performance.PropertyModifyFixed#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_5.cs)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1024: Utilizar las propiedades donde corresponda](../code-quality/ca1024-use-properties-where-appropriate.md)