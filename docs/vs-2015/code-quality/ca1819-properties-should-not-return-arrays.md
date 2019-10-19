---
title: 'CA1819: las propiedades no deben devolver matrices | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PropertiesShouldNotReturnArrays
- CA1819
helpviewer_keywords:
- PropertiesShouldNotReturnArrays
- CA1819
ms.assetid: 85fcf312-57f8-438a-8b10-34441fe0bdeb
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5c85efc3e601eb9e0d887043c50b30587e51321e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668376"
---
# <a name="ca1819-properties-should-not-return-arrays"></a>CA1819: Las propiedades no deberían devolver matrices
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PropertiesShouldNotReturnArrays|
|Identificador de comprobación|CA1819|
|Categoría|Microsoft. performance|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Una propiedad pública o protegida en un tipo público devuelve una matriz.

## <a name="rule-description"></a>Descripción de la regla
 Las matrices devueltas por propiedades no están protegidas contra escritura, aunque la propiedad sea de solo lectura. Para mantener la matriz inviolable, la propiedad debe devolver una copia de la matriz. Por lo general, los usuarios no entienden las implicaciones de rendimiento adversas que se originan al llamar a este tipo de propiedad. En concreto, podrían utilizar la propiedad como una propiedad indizada.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, convierta la propiedad en un método o cambie la propiedad para devolver una colección.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Los atributos pueden contener propiedades que devuelven matrices, pero no pueden contener propiedades que devuelven colecciones. Puede suprimir una advertencia que se genera para una propiedad de un atributo que se deriva de [System. Attribute] (<!-- TODO: review code entity reference <xref:assetId:///System.Attribute?qualifyHint=False&amp;autoUpgrade=True>  -->las. De lo contrario, no suprima una advertencia de esta regla.

## <a name="example-violation"></a>Ejemplo de infracción

### <a name="description"></a>Descripción
 En el ejemplo siguiente se muestra una propiedad que infringe esta regla.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Performance.PropertyArrayViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayViolation/cs/FxCop.Performance.PropertyArrayViolation.cs#1)]
 [!code-vb[FxCop.Performance.PropertyArrayViolation#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayViolation/vb/FxCop.Performance.PropertyArrayViolation.vb#1)]

### <a name="comments"></a>Comentarios
 Para corregir una infracción de esta regla, convierta la propiedad en un método o cambie la propiedad para devolver una colección en lugar de una matriz.

## <a name="change-the-property-to-a-method-example"></a>Cambiar la propiedad a un ejemplo de método

### <a name="description"></a>Descripción
 En el ejemplo siguiente se corrige la infracción mediante el cambio de la propiedad a un método.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Performance.PropertyArrayFixedMethod#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayFixedMethod/cs/FxCop.Performance.PropertyArrayFixedMethod.cs#1)]
 [!code-vb[FxCop.Performance.PropertyArrayFixedMethod#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayFixedMethod/vb/FxCop.Performance.PropertyArrayFixedMethod.vb#1)]

## <a name="return-a-collection-example"></a>Devolver un ejemplo de colección

### <a name="description"></a>Descripción
 En el ejemplo siguiente se corrige la infracción cambiando la propiedad para devolver un

 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>Operador

### <a name="code"></a>Código
 [!code-csharp[FxCop.Performance.PropertyArrayFixedCollection#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayFixedCollection/cs/FxCop.Performance.PropertyArrayFixedCollection.cs#1)]
 [!code-vb[FxCop.Performance.PropertyArrayFixedCollection#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayFixedCollection/vb/FxCop.Performance.PropertyArrayFixedCollection.vb#1)]

## <a name="allowing-users-to-modify-a-property"></a>Permitir a los usuarios modificar una propiedad

### <a name="description"></a>Descripción
 Es posible que desee permitir que el consumidor de la clase modifique una propiedad. En el ejemplo siguiente se muestra una propiedad de lectura y escritura que infringe esta regla.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Performance.PropertyModifyViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyModifyViolation/cs/FxCop.Performance.PropertyModifyViolation.cs#1)]
 [!code-vb[FxCop.Performance.PropertyModifyViolation#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyModifyViolation/vb/FxCop.Performance.PropertyModifyViolation.vb#1)]

### <a name="comments"></a>Comentarios
 En el ejemplo siguiente se corrige la infracción cambiando la propiedad para devolver un <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Performance.PropertyModifyFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyModifyFixed/cs/FxCop.Performance.PropertyModifyFixed.cs#1)]
 [!code-vb[FxCop.Performance.PropertyModifyFixed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyModifyFixed/vb/FxCop.Performance.PropertyModifyFixed.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1024: Utilizar las propiedades donde corresponda](../code-quality/ca1024-use-properties-where-appropriate.md)
