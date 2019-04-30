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
ms.openlocfilehash: c71912fdd70226e1b4be3c14be7c4e0bac26259d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62779851"
---
# <a name="ca1010-collections-should-implement-generic-interface"></a>CA1010: Las colecciones deben implementar la interfaz genérica

|||
|-|-|
|TypeName|CollectionsShouldImplementGenericInterface|
|Identificador de comprobación|CA1010|
|Categoría|Microsoft.Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo

Un tipo implementa la <xref:System.Collections.IEnumerable?displayProperty=fullName> interfaz pero no implementa la <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> interfaz y el contenedor .NET destinos de ensamblado. Esta regla omite los tipos que implementan <xref:System.Collections.IDictionary?displayProperty=fullName>.

De forma predeterminada, esta regla busca solo en tipos visibles externamente, pero se trata de [configurable](#configurability).

## <a name="rule-description"></a>Descripción de la regla

Para ampliar la utilidad de una colección, implemente una de las interfaces de colección genéricas. A continuación, la colección se puede utilizar para rellenar tipos de colección genéricos como los siguientes:

- <xref:System.Collections.Generic.List%601?displayProperty=fullName>
- <xref:System.Collections.Generic.Queue%601?displayProperty=fullName>
- <xref:System.Collections.Generic.Stack%601?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, implemente una de las interfaces de colección genérica siguiente:

- <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>
- <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>
- <xref:System.Collections.Generic.IList%601?displayProperty=fullName>

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

Es seguro suprimir una advertencia de esta regla; Sin embargo, el uso de la colección será más limitado.

## <a name="configurability"></a>Capacidad de configuración

Si ejecuta esta regla de [analizadores de FxCop](install-fxcop-analyzers.md) (y no a través de análisis de código estático), puede configurar qué partes de su código base para ejecutar esta regla en, en función de su accesibilidad. Por ejemplo, para especificar que debe ejecutarse la regla sólo con respecto a la superficie de API no públicos, agregue el siguiente par clave-valor a un archivo .editorconfig en el proyecto:

```
dotnet_code_quality.ca1010.api_surface = private, internal
```

Puede configurar esta opción para simplemente esta regla, para todas las reglas o para todas las reglas de esta categoría (diseño). Para obtener más información, consulte [analizadores de FxCop configurar](configure-fxcop-analyzers.md).

## <a name="example-violation"></a>Infracción de ejemplo

El ejemplo siguiente muestra una clase (tipo de referencia) que se deriva de la no genérica `CollectionBase` (clase), lo que infringe esta regla.

[!code-csharp[FxCop.Design.CollectionsGenericViolation#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_1.cs)]

Para corregir una infracción de esta regla, realice una de las siguientes acciones:

- Implemente las interfaces genéricas.
- Cambie la clase base a un tipo que ya implementa tanto las genéricas y no genéricos interfaces, como la `Collection<T>` clase.

## <a name="fix-by-base-class-change"></a>Corregir por cambio de la clase base

En el ejemplo siguiente se corrige la infracción cambiando la clase base de la colección de la no genérica `CollectionBase` clase para el tipo genérico `Collection<T>` (`Collection(Of T)` en Visual Basic) clase.

[!code-csharp[FxCop.Design.CollectionsGenericBase#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_2.cs)]

Cambiar la clase base de una clase ya se ha publicado se considera un cambio importante para los consumidores existentes.

## <a name="fix-by-interface-implementation"></a>Corregir mediante la implementación de interfaz

En el ejemplo siguiente se corrige la infracción al implementar estas interfaces genéricas: `IEnumerable<T>`, `ICollection<T>`, y `IList<T>` (`IEnumerable(Of T)`, `ICollection(Of T)`, y `IList(Of T)` en Visual Basic).

[!code-csharp[FxCop.Design.CollectionsGenericInterface#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_3.cs)]

## <a name="related-rules"></a>Reglas relacionadas

- [CA1005: Evite parámetros excesivos en tipos genéricos](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)
- [CA1000: No declarar a miembros estáticos en tipos genéricos](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)
- [CA1002: No exponer listas genéricas](../code-quality/ca1002-do-not-expose-generic-lists.md)
- [CA1006: No anidar tipos genéricos en firmas de miembro](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)
- [CA1004: Métodos genéricos deben proporcionar un parámetro de tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)
- [CA1003: Utilizar instancias de controlador de eventos genéricos](../code-quality/ca1003-use-generic-event-handler-instances.md)
- [CA1007: Utilizar valores genéricos cuando sea apropiado](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Vea también

- [Genéricos](/dotnet/csharp/programming-guide/generics/index)