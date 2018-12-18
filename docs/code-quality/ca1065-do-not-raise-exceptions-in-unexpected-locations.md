---
title: 'CA1065: No producir excepciones en ubicaciones inesperadas'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1065
- DoNotRaiseExceptionsInUnexpectedLocations
helpviewer_keywords:
- DoNotRaiseExceptionsInUnexpectedLocations
- CA1065
ms.assetid: 4e1bade4-4ca2-4219-abc3-c7b2d741e157
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4999770367ad7b170398333cf7c7cf2cb9d1c407
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/13/2018
ms.locfileid: "45546699"
---
# <a name="ca1065-do-not-raise-exceptions-in-unexpected-locations"></a>CA1065: No producir excepciones en ubicaciones inesperadas

|||
|-|-|
|TypeName|DoNotRaiseExceptionsInUnexpectedLocations|
|Identificador de comprobación|CA1065|
|Categoría|Microsoft.Design|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo

Un método que no se espera que produzca excepciones inicia una excepción.

## <a name="rule-description"></a>Descripción de la regla

Los métodos que no se esperan que las excepciones se pueden clasificar como sigue:

- Métodos Get de propiedad

- Métodos de descriptor de acceso de eventos

- Es igual a métodos

- Métodos GetHashCode

- Métodos ToString

- Constructores estáticos

- Finalizadores

- Métodos Dispose

- Operadores de igualdad

- Operadores de conversión implícita

Las secciones siguientes tratan estos tipos de método.

### <a name="property-get-methods"></a>Métodos Get de propiedad

Las propiedades son campos básicamente inteligentes. Por lo tanto, deben comportarse como un campo tanto como sea posible. Los campos no producen excepciones ni ustedes tampoco deberían propiedades. Si tiene una propiedad que se produce una excepción, considere la posibilidad de convertirla en un método.

Las siguientes excepciones se pueden iniciar desde un método get de propiedad:

- <xref:System.InvalidOperationException?displayProperty=fullName> y todos los derivados (incluido <xref:System.ObjectDisposedException?displayProperty=fullName>)

- <xref:System.NotSupportedException?displayProperty=fullName> y todos los derivados

- <xref:System.ArgumentException?displayProperty=fullName> (sólo de get indizado)

- <xref:System.Collections.Generic.KeyNotFoundException> (sólo de get indizado)

### <a name="event-accessor-methods"></a>Métodos de descriptor de acceso de eventos

Los descriptores de acceso de eventos deberían ser operaciones simples que no producen excepciones. Un evento no debería producir una excepción al intentar agregar o quitar un controlador de eventos.

Las siguientes excepciones se pueden iniciar desde un descriptor de acceso de eventos:

- <xref:System.InvalidOperationException?displayProperty=fullName> y todos los derivados (incluido <xref:System.ObjectDisposedException?displayProperty=fullName>)

- <xref:System.NotSupportedException?displayProperty=fullName> y todos los derivados

- <xref:System.ArgumentException> y derivados

### <a name="equals-methods"></a>Es igual a métodos

La siguiente **es igual a** métodos no deberían producir excepciones:

- <xref:System.Object.Equals%2A?displayProperty=fullName>

- <xref:System.IEquatable%601.Equals%2A>

Un **es igual a** método debe devolver `true` o `false` en lugar de producir una excepción. Por ejemplo, si no se pasa es igual a dos tipos no coincidentes debe simplemente devolver `false` en lugar de producir una <xref:System.ArgumentException>.

### <a name="gethashcode-methods"></a>Métodos GetHashCode

La siguiente **GetHashCode** métodos normalmente no deberían producir excepciones:

- <xref:System.Object.GetHashCode%2A>

- <xref:System.Collections.IEqualityComparer.GetHashCode%2A>

**GetHashCode** siempre debe devolver un valor. En caso contrario, puede perder los elementos de la tabla hash.

Las versiones de **GetHashCode** que toman un argumento se puede producir un <xref:System.ArgumentException>. Sin embargo, **Object.GetHashCode** nunca debe producir una excepción.

### <a name="tostring-methods"></a>Métodos ToString

El depurador utiliza <xref:System.Object.ToString%2A?displayProperty=fullName> para ayudar a mostrar información acerca de los objetos en formato de cadena. Por lo tanto, **ToString** no debe cambiar el estado de un objeto, y no debería producir excepciones.

### <a name="static-constructors"></a>Constructores estáticos

Iniciar excepciones desde un constructor estático, hace que el tipo que se puede usar en el dominio de aplicación actual. Debe tener una buena razón (por ejemplo, un problema de seguridad) para producir una excepción desde un constructor estático.

### <a name="finalizers"></a>Finalizadores

Producir una excepción de un finalizador, hace que CLR error inmediato, que anula el proceso. Por lo tanto, generar excepciones en un finalizador debe evitarse siempre.

### <a name="dispose-methods"></a>Métodos Dispose

Un <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> método no debería producir una excepción. A menudo se llame a Dispose como parte de la lógica de limpieza en un `finally` cláusula. Por lo tanto, iniciar explícitamente una excepción de Dispose obliga al usuario para agregar el control de excepciones dentro del `finally` cláusula.

El **Dispose (false)** ruta de acceso del código nunca debería producir excepciones porque casi siempre se llama a Dispose de un finalizador.

### <a name="equality-operators--"></a>Operadores de igualdad (==,! =)

Como los métodos Equals, los operadores de igualdad deben devolver `true` o `false`y no debería producir excepciones.

### <a name="implicit-cast-operators"></a>Operadores de conversión implícita

Dado que el usuario suele ser consciente de que se ha llamado un operador de conversión implícita, una excepción producida por el operador de conversión implícita es inesperada. Por lo tanto, no debe producir ninguna excepción de los operadores de conversión implícita.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para los captadores de propiedades, o bien cambie la lógica para que ya no tiene que producir una excepción, o cambiar la propiedad en un método.

Para los demás tipos de método mencionados anteriormente, cambie la lógica para que ya no debe producir una excepción.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

Si se produjo la infracción por una declaración de excepción en lugar de una excepción, es seguro suprimir una advertencia de esta regla.

## <a name="related-rules"></a>Reglas relacionadas

- [CA2219: No producir excepciones en cláusulas de excepción](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)

## <a name="see-also"></a>Vea también

- [Advertencias de diseño](../code-quality/design-warnings.md)