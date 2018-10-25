---
title: 'CA1819: Las propiedades no deberían devolver matrices | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- PropertiesShouldNotReturnArrays
- CA1819
helpviewer_keywords:
- PropertiesShouldNotReturnArrays
- CA1819
ms.assetid: 85fcf312-57f8-438a-8b10-34441fe0bdeb
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6591431edf7ca6de84bbf18d431ad7350308a172
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49881734"
---
# <a name="ca1819-properties-should-not-return-arrays"></a>CA1819: Las propiedades no deberían devolver matrices
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Los atributos pueden contener propiedades que devuelven matrices, pero no pueden contener propiedades que devuelven colecciones. Puede suprimir una advertencia que se genera para una propiedad de un atributo que se deriva de la [System.Attribute] (<!-- TODO: review code entity reference <xref:assetId:///System.Attribute?qualifyHint=False&amp;autoUpgrade=True>  -->) clase. En caso contrario, no suprima una advertencia de esta regla.

## <a name="example-violation"></a>Infracción de ejemplo

### <a name="description"></a>Descripción
 El ejemplo siguiente muestra una propiedad que infringe esta regla.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Performance.PropertyArrayViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayViolation/cs/FxCop.Performance.PropertyArrayViolation.cs#1)]
 [!code-vb[FxCop.Performance.PropertyArrayViolation#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayViolation/vb/FxCop.Performance.PropertyArrayViolation.vb#1)]

### <a name="comments"></a>Comentarios
 Para corregir una infracción de esta regla, que la propiedad de un método o cambie la propiedad para devolver una colección en lugar de una matriz.

## <a name="change-the-property-to-a-method-example"></a>Cambie la propiedad a un ejemplo del método

### <a name="description"></a>Descripción
 El ejemplo siguiente corrige la infracción cambiando la propiedad a un método.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Performance.PropertyArrayFixedMethod#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayFixedMethod/cs/FxCop.Performance.PropertyArrayFixedMethod.cs#1)]
 [!code-vb[FxCop.Performance.PropertyArrayFixedMethod#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayFixedMethod/vb/FxCop.Performance.PropertyArrayFixedMethod.vb#1)]

## <a name="return-a-collection-example"></a>Devolver un ejemplo de la colección

### <a name="description"></a>Descripción
 En el ejemplo siguiente se corrige la infracción cambiando la propiedad para devolver una

 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Performance.PropertyArrayFixedCollection#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayFixedCollection/cs/FxCop.Performance.PropertyArrayFixedCollection.cs#1)]
 [!code-vb[FxCop.Performance.PropertyArrayFixedCollection#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayFixedCollection/vb/FxCop.Performance.PropertyArrayFixedCollection.vb#1)]

## <a name="allowing-users-to-modify-a-property"></a>Lo que permite a los usuarios modificar una propiedad

### <a name="description"></a>Descripción
 Es posible que desee permitir que el consumidor de la clase modificar una propiedad. El ejemplo siguiente muestra una propiedad de lectura/escritura que infringe esta regla.

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



