---
title: 'CA1010: Las colecciones deben implementar la interfaz genérica'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cb43481b80726171414fab6b6a65fee8a5e29cb0
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="ca1010-collections-should-implement-generic-interface"></a>CA1010: Las colecciones deben implementar la interfaz genérica
|||
|-|-|
|TypeName|CollectionsShouldImplementGenericInterface|
|Identificador de comprobación|CA1010|
|Categoría|Microsoft.Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Un tipo visible externamente implementa la <xref:System.Collections.IEnumerable?displayProperty=fullName> interfaz pero no implementa la <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> interfaz y los destinos de ensamblado que lo contiene [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]. Esta regla omite los tipos que implementan <xref:System.Collections.IDictionary?displayProperty=fullName>.

## <a name="rule-description"></a>Descripción de la regla
 Para ampliar la utilidad de una colección, implemente una de las interfaces de colección genéricas. A continuación, la colección se puede utilizar para rellenar tipos de colección genéricos como los siguientes:

-   <xref:System.Collections.Generic.List%601?displayProperty=fullName>

-   <xref:System.Collections.Generic.Queue%601?displayProperty=fullName>

-   <xref:System.Collections.Generic.Stack%601?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, implemente una de las interfaces de colección genérica siguiente:

-   <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>

-   <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>

-   <xref:System.Collections.Generic.IList%601?displayProperty=fullName>

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla; Sin embargo, la colección tendrá un uso más limitado.

## <a name="example-violation"></a>Infracción de ejemplo

### <a name="description"></a>Descripción
 En el ejemplo siguiente se muestra una clase (tipo de referencia) que se deriva de la no genérica `CollectionBase` (clase), lo que infringe esta regla.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Design.CollectionsGenericViolation#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_1.cs)]

### <a name="comments"></a>Comentarios
 Para corregir una infracción de esta infracción, debe implementar las interfaces genéricas o cambiar la clase base a un tipo que ya implementa tanto las genéricas y no genéricos interfaces, como la `Collection<T>` clase.

## <a name="fix-by-base-class-change"></a>Corregir por cambio de clase Base

### <a name="description"></a>Descripción
 En el ejemplo siguiente se corrige la infracción cambiando la clase base de la colección de no genérica `CollectionBase` clase a la interfaz genérica `Collection<T>` (`Collection(Of T)` en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) clase.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Design.CollectionsGenericBase#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_2.cs)]

### <a name="comments"></a>Comentarios
 Cambiar la clase base de una clase ya se ha liberado se considera un cambio importante para los consumidores.

## <a name="fix-by-interface-implementation"></a>Corregir por implementación de interfaz

### <a name="description"></a>Descripción
 En el ejemplo siguiente se corrige la infracción al implementar estas interfaces genéricas: `IEnumerable<T>`, `ICollection<T>`, y `IList<T>` (`IEnumerable(Of T)`, `ICollection(Of T)`, y `IList(Of T)` en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).

### <a name="code"></a>Código
 [!code-csharp[FxCop.Design.CollectionsGenericInterface#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_3.cs)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1005: Evite parámetros excesivos en tipos genéricos](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1000: No declarar miembros estáticos en tipos genéricos](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: No exponer listas genéricas](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: No anidar tipos genéricos en firmas de miembro](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: Los métodos genéricos deben proporcionar un parámetro de tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: Utilizar instancias genéricas de controlador de eventos](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: Utilizar valores genéricos cuando sea posible](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Vea también
 [Genéricos](/dotnet/csharp/programming-guide/generics/index)