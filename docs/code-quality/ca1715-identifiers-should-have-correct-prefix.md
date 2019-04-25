---
title: 'CA1715: Los identificadores deben tener el prefijo correcto'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1715
- IdentifiersShouldHaveCorrectPrefix
helpviewer_keywords:
- IdentifiersShouldHaveCorrectPrefix
- CA1715
ms.assetid: cf45f8df-6855-4cb6-a4e2-7cfed714cf2f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: b794eb7c7a258a843763b2c68902000031c17eb3
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57873609"
---
# <a name="ca1715-identifiers-should-have-correct-prefix"></a>CA1715: Los identificadores deben tener el prefijo correcto

|||
|-|-|
|TypeName|IdentifiersShouldHaveCorrectPrefix|
|Identificador de comprobación|CA1715|
|Categoría|Microsoft.Naming|
|Cambio problemático|Problemático: cuando se desencadena en interfaces.<br /><br /> Indivisible - cuando se genera en parámetros de tipo genérico.|

## <a name="cause"></a>Motivo

El nombre de una interfaz no se inicia con una mayúscula 'I'.

O bien

El nombre de un [parámetro de tipo genérico](/dotnet/csharp/programming-guide/generics/generic-type-parameters) en un tipo o método no se inicia con una mayúscula ' t '.

De forma predeterminada, esta regla busca solo en interfaces visibles externamente, tipos y métodos, pero se trata de [configurable](#configurability).

## <a name="rule-description"></a>Descripción de la regla

Por convención, los nombres de ciertos elementos de programación se inicie con un prefijo específico.

Nombres de interfaz deben empezar con una mayúscula 'I' seguida de otra letra mayúscula. Esta regla notifica las infracciones de nombres de interfaz como 'MyInterface' y 'IsolatedInterface'.

Los nombres de parámetro de tipo genérico deben comenzar con una mayúscula ' t ' y, opcionalmente, puede ir seguida por otra letra mayúscula. Esta regla notifica las infracciones de los nombres de parámetro de tipo genérico, como 'V' y 'Type'.

Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime. Esto reduce la curva de aprendizaje necesaria para las nuevas bibliotecas de software y aumenta la confianza del cliente respecto a que la biblioteca se haya desarrollado por parte de un especialista en desarrollo de código administrado.

## <a name="configurability"></a>Capacidad de configuración

Si ejecuta esta regla de [analizadores de FxCop](install-fxcop-analyzers.md) (y no a través de análisis de código estático), puede configurar esta regla analiza de qué partes del código. Para obtener más información, consulte [analizadores de FxCop configurar](configure-fxcop-analyzers.md).

### <a name="single-character-type-parameters"></a>Parámetros de tipo de carácter único

Puede configurar si se deben excluir de los parámetros de tipo de carácter único de esta regla. Por ejemplo, para especificar que esta regla *no debería* analizar parámetros de tipo de carácter único, agregue uno de los siguientes pares clave-valor a un archivo .editorconfig en el proyecto:

```
# Package version 2.9.0 and later
dotnet_code_quality.CA1715.exclude_single_letter_type_parameters = true

# Package version 2.6.3 and earlier
dotnet_code_quality.CA2007.allow_single_letter_type_parameters = true
```

> [!NOTE]
> Esta regla se desencadena nunca de un parámetro de tipo denominado `T`, por ejemplo, `Collection<T>`.

### <a name="api-surface"></a>Superficie de API

Puede configurar qué partes de su código base para ejecutar esta regla en, en función de su accesibilidad. Por ejemplo, para especificar que debe ejecutarse la regla sólo con respecto a la superficie de API no públicos, agregue el siguiente par clave-valor a un archivo .editorconfig en el proyecto:

```
dotnet_code_quality.ca1715.api_surface = private, internal
```

Puede configurar esta opción para simplemente esta regla, para todas las reglas o para todas las reglas de esta categoría (convenciones de nomenclatura).

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Cambie el nombre el identificador se incluyen el prefijo correctamente.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

No suprima las advertencias de esta regla.

## <a name="interface-naming-example"></a>Ejemplo de un nombre de interfaz

El fragmento de código siguiente muestra una interfaz denominada incorrectamente:

[!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_1.cpp)]
[!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_1.vb)]
[!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_1.cs)]

El fragmento de código siguiente corrige la infracción anterior agregando el prefijo de la interfaz 'I':

[!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_2.cs)]
[!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_2.cpp)]
[!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_2.vb)]

## <a name="type-parameter-naming-example"></a>Ejemplo de asignación de nombres de parámetro de tipo

El fragmento de código siguiente muestra un parámetro de tipo genérico incorrectamente con nombre:

[!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_3.cpp)]
[!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_3.vb)]
[!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_3.cs)]

El fragmento de código siguiente corrige la infracción anterior agregando el prefijo de parámetro de tipo genérico ' t ':

[!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_4.cpp)]
[!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_4.cs)]
[!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_4.vb)]

## <a name="related-rules"></a>Reglas relacionadas

- [CA1722: Los identificadores no deberían tener el prefijo incorrecto](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)