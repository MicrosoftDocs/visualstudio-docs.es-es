---
title: 'CA1010: Las colecciones deben implementar la interfaz genérica'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1010
- CollectionsShouldImplementGenericInterface
helpviewer_keywords:
- CA1010
- CollectionsShouldImplementGenericInterface
ms.assetid: c7d7126f-fa70-40be-8f93-3243e1760dc5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 70a418b211cd4340dba9c15f0bf52e3cdfdf8e8f
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547905"
---
# <a name="ca1010-collections-should-implement-generic-interface"></a>CA1010: Las colecciones deben implementar la interfaz genérica

|||
|-|-|
|TypeName|CollectionsShouldImplementGenericInterface|
|Identificador de comprobación|CA1010|
|Categoría|Microsoft.Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Causa

Un tipo implementa la <xref:System.Collections.IEnumerable?displayProperty=fullName> interfaz pero no implementa la <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> interfaz, y el ensamblado contenedor tiene como destino .net. Esta regla omite los tipos que implementan <xref:System.Collections.IDictionary?displayProperty=fullName>.

De forma predeterminada, esta regla solo examina los tipos visibles externamente, pero esto es [configurable](#configurability).

## <a name="rule-description"></a>Descripción de la regla

Para ampliar la utilidad de una colección, implemente una de las interfaces de colección genéricas. A continuación, la colección se puede usar para rellenar tipos de colección genéricos como los siguientes:

- <xref:System.Collections.Generic.List%601?displayProperty=fullName>
- <xref:System.Collections.Generic.Queue%601?displayProperty=fullName>
- <xref:System.Collections.Generic.Stack%601?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, implemente una de las interfaces de colección genéricas siguientes:

- <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>
- <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>
- <xref:System.Collections.Generic.IList%601?displayProperty=fullName>

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

Es seguro suprimir una advertencia de esta regla. sin embargo, el uso de la colección será más limitado.

## <a name="configurability"></a>Configurabilidad

Si está ejecutando esta regla desde los [analizadores de FxCop](install-fxcop-analyzers.md) (y no con el análisis heredado), puede configurar en qué partes del código base ejecutar esta regla, según su accesibilidad. Por ejemplo, para especificar que la regla se debe ejecutar solo en la superficie de API no pública, agregue el siguiente par clave-valor a un archivo. editorconfig en el proyecto:

```ini
dotnet_code_quality.ca1010.api_surface = private, internal
```

Puede configurar esta opción solo para esta regla, para todas las reglas o para todas las reglas de esta categoría (diseño). Para obtener más información, vea [configurar analizadores de FxCop](configure-fxcop-analyzers.md).

## <a name="example-violation"></a>Ejemplo de infracción

En el ejemplo siguiente se muestra una clase (tipo de referencia) que se deriva de la `CollectionBase` clase no genérica, que infringe esta regla.

[!code-csharp[FxCop.Design.CollectionsGenericViolation#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_1.cs)]

Para corregir una infracción de esta regla, realice una de las siguientes acciones:

- Implemente las interfaces genéricas.
- Cambie la clase base a un tipo que ya implemente las interfaces genéricas y no genéricas, como la `Collection<T>` clase.

## <a name="fix-by-base-class-change"></a>Corregir por cambio de clase base

En el ejemplo siguiente se corrige la infracción mediante el cambio de la clase base de la colección `CollectionBase` de la clase no `Collection<T>` genérica`Collection(Of T)` a la clase genérica (en Visual Basic).

[!code-csharp[FxCop.Design.CollectionsGenericBase#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_2.cs)]

Cambiar la clase base de una clase ya liberada se considera un cambio importante para los consumidores existentes.

## <a name="fix-by-interface-implementation"></a>Corrección por implementación de interfaz

En el ejemplo siguiente se corrige la infracción mediante la implementación `IEnumerable<T>`de `ICollection<T>`estas interfaces `IList<T>` genéricas:, `IList(Of T)` y (`IEnumerable(Of T)`, `ICollection(Of T)`y en Visual Basic).

[!code-csharp[FxCop.Design.CollectionsGenericInterface#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_3.cs)]

## <a name="related-rules"></a>Reglas relacionadas

- [CA1005: Evite parámetros excesivos en tipos genéricos](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)
- [CA1000: No declarar miembros estáticos en tipos genéricos](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)
- [CA1002: No exponer listas genéricas](../code-quality/ca1002-do-not-expose-generic-lists.md)
- [CA1006: No anide tipos genéricos en firmas de miembro](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)
- [CA1004: Los métodos genéricos deben proporcionar un parámetro de tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)
- [CA1003: Usar instancias de controlador de eventos genéricos](../code-quality/ca1003-use-generic-event-handler-instances.md)
- [CA1007: Usar genéricos cuando sea necesario](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Vea también

- [Genéricos](/dotnet/csharp/programming-guide/generics/index)