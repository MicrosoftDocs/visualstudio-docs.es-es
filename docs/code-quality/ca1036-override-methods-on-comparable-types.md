---
title: 'CA1036: Invalidar métodos en tipos comparables'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1036
- OverrideMethodsOnComparableTypes
helpviewer_keywords:
- OverrideMethodsOnComparableTypes
- CA1036
ms.assetid: 2329f844-4cb8-426d-bee2-cd065d1346d0
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 12b00c202373310b04021a46e74af2af7e10d535
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62779001"
---
# <a name="ca1036-override-methods-on-comparable-types"></a>CA1036: Invalidar métodos en tipos comparables

|||
|-|-|
|TypeName|OverrideMethodsOnComparableTypes|
|Identificador de comprobación|CA1036|
|Categoría|Microsoft.Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo

Un tipo implementa la <xref:System.IComparable?displayProperty=fullName> interfaz y no invalida <xref:System.Object.Equals%2A?displayProperty=fullName> o no sobrecarga el operador específico del lenguaje para la igualdad, desigualdad, menor-que o mayor-que. La regla no informa de una infracción si el tipo hereda solo una implementación de la interfaz.

De forma predeterminada, esta regla solo se examina los tipos públicos y protegidos, pero se trata de [configurable](#configurability).

## <a name="rule-description"></a>Descripción de la regla

Los tipos que definen un criterio de ordenación personalizados implementan la <xref:System.IComparable> interfaz. El <xref:System.IComparable.CompareTo%2A> método devuelve un valor entero que indica el orden correcto para que dos instancias del tipo. Esta regla identifica los tipos que establezca un criterio de ordenación. Establecer un criterio de ordenación implica que el significado normal de igualdad, desigualdad, menor-que y mayor-que no son aplicables. Cuando se proporciona una implementación de <xref:System.IComparable>, normalmente debe invalidar también <xref:System.Object.Equals%2A> para que devuelva valores que sean coherentes con <xref:System.IComparable.CompareTo%2A>. Si invalida <xref:System.Object.Equals%2A> y son de codificación en un lenguaje que admite las sobrecargas de operador, también debe proporcionar los operadores que son coherentes con <xref:System.Object.Equals%2A>.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, invalidar <xref:System.Object.Equals%2A>. Si su lenguaje de programación admite la sobrecarga de operadores, proporcione los siguientes operadores:

- op_Equality
- op_Inequality
- op_LessThan
- op_GreaterThan

En C#, los tokens que se usan para representar estos operadores son los siguientes:

```csharp
==
!=
<
>
```

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

Es seguro suprimir una advertencia de regla CA1036 si se ha provocado la infracción a la falta de operadores y el lenguaje de programación no admite la sobrecarga de operadores, como sucede con Visual Basic. Si determina que la implementación de los operadores no tiene sentido en el contexto de la aplicación, también es seguro suprimir una advertencia de esta regla cuando se desencadena en los operadores de igualdad distintos op_Equality. Sin embargo, debe invalidar siempre op_Equality y el operador == si invalida <xref:System.Object.Equals%2A?displayProperty=nameWithType>.

## <a name="configurability"></a>Capacidad de configuración

Si ejecuta esta regla de [analizadores de FxCop](install-fxcop-analyzers.md) (y no a través de análisis de código estático), puede configurar qué partes de su código base para ejecutar esta regla en, en función de su accesibilidad. Por ejemplo, para especificar que debe ejecutarse la regla sólo con respecto a la superficie de API no públicos, agregue el siguiente par clave-valor a un archivo .editorconfig en el proyecto:

```
dotnet_code_quality.ca1036.api_surface = private, internal
```

Puede configurar esta opción para simplemente esta regla, para todas las reglas o para todas las reglas de esta categoría (diseño). Para obtener más información, consulte [analizadores de FxCop configurar](configure-fxcop-analyzers.md).

## <a name="examples"></a>Ejemplos

El código siguiente contiene un tipo que implementa correctamente <xref:System.IComparable>. Comentarios de código identifican los métodos que satisfacen diversas reglas que están relacionados con <xref:System.Object.Equals%2A> y <xref:System.IComparable> interfaz.

[!code-csharp[FxCop.Design.IComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_1.cs)]

El siguiente código de aplicación comprueba el comportamiento de la <xref:System.IComparable> implementación que se mostró anteriormente.

[!code-csharp[FxCop.Design.TestIComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_2.cs)]

## <a name="see-also"></a>Vea también

- <xref:System.IComparable?displayProperty=fullName>
- <xref:System.Object.Equals%2A?displayProperty=fullName>
- [Operadores de igualdad](/dotnet/standard/design-guidelines/equality-operators)