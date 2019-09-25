---
title: 'CA1710: Los identificadores deben tener un sufijo correcto'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1710
- IdentifiersShouldHaveCorrectSuffix
helpviewer_keywords:
- IdentifiersShouldHaveCorrectSuffix
- CA1710
ms.assetid: 2b8e6dce-b4e8-4a66-ba9a-6b79be5bfe8c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 50c67c614c4ece8f1925f4133f749a1c5747fe31
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234164"
---
# <a name="ca1710-identifiers-should-have-correct-suffix"></a>CA1710: Los identificadores deben tener un sufijo correcto

|||
|-|-|
|TypeName|IdentifiersShouldHaveCorrectSuffix|
|Identificador de comprobación|CA1710|
|Categoría|Microsoft.Naming|
|Cambio importante|Problemático|

## <a name="cause"></a>Motivo

Un identificador no tiene el sufijo correcto.

De forma predeterminada, esta regla solo examina los identificadores visibles externamente, pero esto es [configurable](#configurability).

## <a name="rule-description"></a>Descripción de la regla

Por Convención, los nombres de tipos que extienden determinados tipos base o que implementan determinadas interfaces, o tipos derivados de estos tipos, tienen un sufijo que está asociado con el tipo base o la interfaz.

Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime. Esto reduce la curva de aprendizaje necesaria para las nuevas bibliotecas de software y aumenta la confianza del cliente respecto a que la biblioteca se haya desarrollado por parte de un especialista en desarrollo de código administrado.

En la tabla siguiente se enumeran los tipos base y las interfaces que tienen sufijos asociados.

|Tipo base/Interfaz|Sufijo|
|--------------------------|------------|
|<xref:System.Attribute?displayProperty=fullName>|Atributo|
|<xref:System.EventArgs?displayProperty=fullName>|EventArgs|
|<xref:System.Exception?displayProperty=fullName>|Excepción|
|<xref:System.Collections.ICollection?displayProperty=fullName>|Collection|
|<xref:System.Collections.IDictionary?displayProperty=fullName>|Dictionary|
|<xref:System.Collections.IEnumerable?displayProperty=fullName>|Collection|
|<xref:System.Collections.Queue?displayProperty=fullName>|Colección o cola|
|<xref:System.Collections.Stack?displayProperty=fullName>|Colección o pila|
|<xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>|Collection|
|<xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|Dictionary|
|<xref:System.Data.DataSet?displayProperty=fullName>|DataSet|
|<xref:System.Data.DataTable?displayProperty=fullName>|Colección o DataTable|
|<xref:System.IO.Stream?displayProperty=fullName>|Secuencia|
|<xref:System.Security.IPermission?displayProperty=fullName>|Permiso|
|<xref:System.Security.Policy.IMembershipCondition?displayProperty=fullName>|Condición|
|Delegado de controlador de eventos.|EventHandler|

Los tipos que <xref:System.Collections.ICollection> implementan y son un tipo generalizado de estructura de datos, como un diccionario, una pila o una cola, son nombres permitidos que proporcionan información significativa sobre el uso previsto del tipo.

Los tipos que <xref:System.Collections.ICollection> implementan y son una colección de elementos específicos tienen nombres que terminan con la palabra ' Collection '. Por ejemplo, una colección de <xref:System.Collections.Queue> objetos tendría el nombre "QueueCollection". El sufijo ' Collection ' indica que los miembros de la colección se pueden enumerar mediante la `foreach` instrucción (`For Each` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).

Los tipos que <xref:System.Collections.IDictionary> implementan tienen nombres que terminan con la palabra ' Dictionary ' incluso si el tipo <xref:System.Collections.IEnumerable> también <xref:System.Collections.ICollection>implementa o. Las convenciones de nomenclatura de los sufijos ' Collection ' y ' Dictionary ' permiten a los usuarios distinguir entre los dos patrones de enumeración siguientes.

Los tipos con el sufijo ' Collection ' siguen este patrón de enumeración.

```
foreach(SomeType x in SomeCollection) { }
```

Los tipos con el sufijo ' Dictionary ' siguen este patrón de enumeración.

```
foreach(SomeType x in SomeDictionary.Values) { }
```

Un <xref:System.Data.DataSet> objeto consta de una colección de <xref:System.Data.DataTable> objetos, que se componen <xref:System.Data.DataColumn?displayProperty=fullName> de <xref:System.Data.DataRow?displayProperty=fullName> colecciones de objetos y, entre otros. Estas colecciones se <xref:System.Collections.ICollection> implementan a <xref:System.Data.InternalDataCollectionBase?displayProperty=fullName> través de la clase base.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Cambie el nombre del tipo para que tenga como sufijo el término correcto.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

Es seguro suprimir una advertencia para usar el sufijo ' Collection ' si el tipo es una estructura de datos generalizada que podría extenderse o que contendrá un conjunto arbitrario de diversos elementos. En este caso, un nombre que proporcione información significativa sobre la implementación, el rendimiento u otras características de la estructura de datos podría tener sentido (por ejemplo, BinaryTree). En los casos en los que el tipo representa una colección de un tipo específico (por ejemplo, StringCollection), no suprima una advertencia de esta regla porque el sufijo indica que el tipo se puede enumerar `foreach` mediante una instrucción.

En el caso de otros sufijos, no suprima una advertencia de esta regla. El sufijo permite que el uso previsto sea evidente a partir del nombre de tipo.

## <a name="configurability"></a>Configurabilidad

Si está ejecutando esta regla desde los [analizadores de FxCop](install-fxcop-analyzers.md) (y no con el análisis heredado), puede configurar en qué partes del código base ejecutar esta regla, según su accesibilidad. Por ejemplo, para especificar que la regla se debe ejecutar solo en la superficie de API no pública, agregue el siguiente par clave-valor a un archivo. editorconfig en el proyecto:

```ini
dotnet_code_quality.ca1710.api_surface = private, internal
```

Puede configurar esta opción solo para esta regla, para todas las reglas o para todas las reglas de esta categoría (nomenclatura). Para obtener más información, vea [configurar analizadores de FxCop](configure-fxcop-analyzers.md).

## <a name="related-rules"></a>Reglas relacionadas

[CA1711: Los identificadores no deben tener un sufijo incorrecto](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

## <a name="see-also"></a>Vea también

- [Atributos](/dotnet/standard/design-guidelines/attributes)
- [Control y generación de eventos](/dotnet/standard/events/index)