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
ms.openlocfilehash: 11209ec181e2c2b61c7767787ee99c2d69eabe8b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62545568"
---
# <a name="ca1819-properties-should-not-return-arrays"></a>CA1819: Las propiedades no deben devolver matrices

|||
|-|-|
|TypeName|PropertiesShouldNotReturnArrays|
|Identificador de comprobación|CA1819|
|Categoría|Microsoft.Performance|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo

Una propiedad devuelve una matriz.

De forma predeterminada, esta regla solo se examina las propiedades visibles externamente y tipos, pero se trata de [configurable](#configurability).

## <a name="rule-description"></a>Descripción de la regla

Matrices devueltas por las propiedades no están protegidos contra escritura, incluso si la propiedad es de solo lectura. Para mantener la matriz inviolable, la propiedad debe devolver una copia de la matriz. Por lo general, los usuarios no entienden las implicaciones de rendimiento adversas de llamar a este tipo de propiedad. En concreto, puede usar la propiedad como una propiedad indizada.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, que la propiedad de un método o cambie la propiedad para devolver una colección.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

Puede suprimir una advertencia que se genera para una propiedad de un atributo que se deriva el <xref:System.Attribute> clase. Los atributos pueden contener propiedades que devuelven matrices, pero no pueden contener propiedades que devuelven colecciones.

Puede suprimir la advertencia si la propiedad forma parte de un [el objeto de transferencia de datos (DTO)](/previous-versions/msp-n-p/ff649585(v=pandp.10)) clase.

En caso contrario, no suprima una advertencia de esta regla.

## <a name="configurability"></a>Capacidad de configuración

Si ejecuta esta regla de [analizadores de FxCop](install-fxcop-analyzers.md) (y no a través de análisis de código estático), puede configurar qué partes de su código base para ejecutar esta regla en, en función de su accesibilidad. Por ejemplo, para especificar que debe ejecutarse la regla sólo con respecto a la superficie de API no públicos, agregue el siguiente par clave-valor a un archivo .editorconfig en el proyecto:

```
dotnet_code_quality.ca1819.api_surface = private, internal
```

Puede configurar esta opción para simplemente esta regla, para todas las reglas o para todas las reglas de esta categoría (rendimiento). Para obtener más información, consulte [analizadores de FxCop configurar](configure-fxcop-analyzers.md).

## <a name="example-violation"></a>Infracción de ejemplo

El ejemplo siguiente muestra una propiedad que infringe esta regla:

[!code-csharp[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_1.cs)]
[!code-vb[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_1.vb)]

Para corregir una infracción de esta regla, que la propiedad de un método o cambie la propiedad para devolver una colección en lugar de una matriz.

### <a name="change-the-property-to-a-method"></a>Cambie la propiedad a un método

El ejemplo siguiente corrige la infracción cambiando la propiedad a un método:

[!code-vb[FxCop.Performance.PropertyArrayFixedMethod#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_2.vb)]
[!code-csharp[FxCop.Performance.PropertyArrayFixedMethod#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_2.cs)]

### <a name="change-the-property-to-return-a-collection"></a>Cambie la propiedad para devolver una colección

En el ejemplo siguiente se corrige la infracción cambiando la propiedad para devolver un <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>:

[!code-csharp[FxCop.Performance.PropertyArrayFixedCollection#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_3.cs)]
[!code-vb[FxCop.Performance.PropertyArrayFixedCollection#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_3.vb)]

## <a name="allow-users-to-modify-a-property"></a>Permitir a los usuarios modificar una propiedad

Es posible que desee permitir que el consumidor de la clase modificar una propiedad. El ejemplo siguiente muestra una propiedad de lectura/escritura que infringe esta regla:

[!code-csharp[FxCop.Performance.PropertyModifyViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_4.cs)]
[!code-vb[FxCop.Performance.PropertyModifyViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_4.vb)]

En el ejemplo siguiente se corrige la infracción cambiando la propiedad para devolver un <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>:

[!code-vb[FxCop.Performance.PropertyModifyFixed#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_5.vb)]
[!code-csharp[FxCop.Performance.PropertyModifyFixed#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_5.cs)]

## <a name="related-rules"></a>Reglas relacionadas

- [CA1024: Utilizar las propiedades donde corresponda](../code-quality/ca1024-use-properties-where-appropriate.md)