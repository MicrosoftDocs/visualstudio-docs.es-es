---
title: 'CA1819: Las propiedades no deben devolver matrices'
ms.date: 03/11/2019
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
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 053cb4c55362a4f51b7c8e8049214aa41773f373
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233451"
---
# <a name="ca1819-properties-should-not-return-arrays"></a>CA1819: Las propiedades no deben devolver matrices

|||
|-|-|
|TypeName|PropertiesShouldNotReturnArrays|
|Identificador de comprobación|CA1819|
|Categoría|Microsoft.Performance|
|Cambio importante|Problemático|

## <a name="cause"></a>Motivo

Una propiedad devuelve una matriz.

De forma predeterminada, esta regla solo examina las propiedades y los tipos visibles externamente, pero esto es [configurable](#configurability).

## <a name="rule-description"></a>Descripción de la regla

Las matrices devueltas por propiedades no están protegidas contra escritura, aunque la propiedad sea de solo lectura. Para mantener la matriz inviolable, la propiedad debe devolver una copia de la matriz. Normalmente, los usuarios no comprenderán las implicaciones adversas en el rendimiento de la llamada a este tipo de propiedad. En concreto, podrían utilizar la propiedad como una propiedad indizada.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, convierta la propiedad en un método o cambie la propiedad para devolver una colección.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

Puede suprimir una advertencia que se genera para una propiedad de un atributo que se deriva de la <xref:System.Attribute> clase. Los atributos pueden contener propiedades que devuelven matrices, pero no pueden contener propiedades que devuelven colecciones.

Puede suprimir la advertencia si la propiedad forma parte de una clase de [objeto transferencia de datos (DTO)](/previous-versions/msp-n-p/ff649585(v=pandp.10)) .

De lo contrario, no suprima una advertencia de esta regla.

## <a name="configurability"></a>Configurabilidad

Si está ejecutando esta regla desde los [analizadores de FxCop](install-fxcop-analyzers.md) (y no con el análisis heredado), puede configurar en qué partes del código base ejecutar esta regla, según su accesibilidad. Por ejemplo, para especificar que la regla se debe ejecutar solo en la superficie de API no pública, agregue el siguiente par clave-valor a un archivo. editorconfig en el proyecto:

```ini
dotnet_code_quality.ca1819.api_surface = private, internal
```

Puede configurar esta opción solo para esta regla, para todas las reglas o para todas las reglas de esta categoría (rendimiento). Para obtener más información, vea [configurar analizadores de FxCop](configure-fxcop-analyzers.md).

## <a name="example-violation"></a>Ejemplo de infracción

En el ejemplo siguiente se muestra una propiedad que infringe esta regla:

[!code-csharp[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_1.cs)]
[!code-vb[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_1.vb)]

Para corregir una infracción de esta regla, convierta la propiedad en un método o cambie la propiedad para devolver una colección en lugar de una matriz.

### <a name="change-the-property-to-a-method"></a>Cambiar la propiedad a un método

En el ejemplo siguiente se corrige la infracción mediante el cambio de la propiedad a un método:

[!code-vb[FxCop.Performance.PropertyArrayFixedMethod#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_2.vb)]
[!code-csharp[FxCop.Performance.PropertyArrayFixedMethod#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_2.cs)]

### <a name="change-the-property-to-return-a-collection"></a>Cambiar la propiedad para devolver una colección

En el ejemplo siguiente se corrige la infracción cambiando la propiedad para <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>devolver:

[!code-csharp[FxCop.Performance.PropertyArrayFixedCollection#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_3.cs)]
[!code-vb[FxCop.Performance.PropertyArrayFixedCollection#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_3.vb)]

## <a name="allow-users-to-modify-a-property"></a>Permitir a los usuarios modificar una propiedad

Es posible que desee permitir que el consumidor de la clase modifique una propiedad. En el ejemplo siguiente se muestra una propiedad de lectura y escritura que infringe esta regla:

[!code-csharp[FxCop.Performance.PropertyModifyViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_4.cs)]
[!code-vb[FxCop.Performance.PropertyModifyViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_4.vb)]

En el ejemplo siguiente se corrige la infracción cambiando la propiedad para <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>devolver:

[!code-vb[FxCop.Performance.PropertyModifyFixed#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_5.vb)]
[!code-csharp[FxCop.Performance.PropertyModifyFixed#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_5.cs)]

## <a name="related-rules"></a>Reglas relacionadas

- [CA1024: Usar propiedades cuando corresponda](../code-quality/ca1024-use-properties-where-appropriate.md)