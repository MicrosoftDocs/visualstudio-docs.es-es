---
title: 'CA1065: no producir excepciones en ubicaciones inesperadas | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1065
- DoNotRaiseExceptionsInUnexpectedLocations
helpviewer_keywords:
- DoNotRaiseExceptionsInUnexpectedLocations
- CA1065
ms.assetid: 4e1bade4-4ca2-4219-abc3-c7b2d741e157
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 4b49ea9c293128efd400a1aa22d78ae4ee945092
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663599"
---
# <a name="ca1065-do-not-raise-exceptions-in-unexpected-locations"></a>CA1065: No producir excepciones en ubicaciones inesperadas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotRaiseExceptionsInUnexpectedLocations|
|Identificador de comprobación|CA1065|
|Categoría|Microsoft. Design|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 Un método que no se espera que produzca excepciones inicia una excepción.

## <a name="rule-description"></a>Descripción de la regla
 Los métodos que no se espera que produzcan excepciones se pueden categorizar de la manera siguiente:

- Métodos Get de propiedad

- Métodos de descriptor de acceso de eventos

- Equals (métodos)

- GetHashCode (métodos)

- ToString (métodos)

- Constructores estáticos

- Finalizadores

- Métodos Dispose

- Operadores de igualdad

- Operadores de conversión implícita

  En las secciones siguientes se describen estos tipos de método.

### <a name="property-get-methods"></a>Métodos Get de propiedad
 Las propiedades son básicamente campos inteligentes. Por lo tanto, deben comportarse como un campo lo máximo posible. Los campos no producen excepciones y no tienen ninguna propiedad. Si tiene una propiedad que inicia una excepción, considere la posibilidad de convertirla en un método.

 Se permite que se inicien las siguientes excepciones desde un método get de propiedad:

- <xref:System.InvalidOperationException?displayProperty=fullName> y todos los derivados (incluido <xref:System.ObjectDisposedException?displayProperty=fullName>)

- <xref:System.NotSupportedException?displayProperty=fullName> y todos los derivados

- <xref:System.ArgumentException?displayProperty=fullName> (solo desde Get indizado)

- <xref:System.Collections.Generic.KeyNotFoundException> (solo desde Get indizado)

### <a name="event-accessor-methods"></a>Métodos de descriptor de acceso de eventos
 Los descriptores de acceso de eventos deben ser operaciones simples que no inician excepciones. Un evento no debe producir una excepción al intentar agregar o quitar un controlador de eventos.

 Se permite que se inicien las siguientes excepciones desde un decedidor de eventos:

- <xref:System.InvalidOperationException?displayProperty=fullName> y todos los derivados (incluido <xref:System.ObjectDisposedException?displayProperty=fullName>)

- <xref:System.NotSupportedException?displayProperty=fullName> y todos los derivados

- <xref:System.ArgumentException> y derivados

### <a name="equals-methods"></a>Equals (métodos)
 Los siguientes métodos **Equals** no deben producir excepciones:

- <xref:System.Object.Equals%2A?displayProperty=fullName>

- [M:IEquatable.Equals](http://go.microsoft.com/fwlink/?LinkId=113472)

  Un método **Equals** debe devolver `true` o `false` en lugar de producir una excepción. Por ejemplo, si se pasan dos tipos no coincidentes, solo se debe devolver `false` en lugar de producir un <xref:System.ArgumentException>.

### <a name="gethashcode-methods"></a>GetHashCode (métodos)
 Los siguientes métodos **GetHashCode** normalmente no deben producir excepciones:

- <xref:System.Object.GetHashCode%2A>

- [M:IEqualityComparer.GetHashCode (T)](http://go.microsoft.com/fwlink/?LinkId=113477)

  **GetHashCode** siempre debe devolver un valor. De lo contrario, puede perder elementos en la tabla hash.

  Las versiones de **GetHashCode** que toman un argumento pueden producir una <xref:System.ArgumentException>. Sin embargo, **Object. GetHashCode** nunca debe producir una excepción.

### <a name="tostring-methods"></a>ToString (métodos)
 El depurador utiliza <xref:System.Object.ToString%2A?displayProperty=fullName> para ayudar a mostrar información sobre los objetos en formato de cadena. Por lo tanto, **ToString** no debe cambiar el estado de un objeto y no debe producir excepciones.

### <a name="static-constructors"></a>Constructores estáticos
 Producir excepciones desde un constructor estático hace que el tipo sea inutilizable en el dominio de aplicación actual. Debe tener una buena razón (por ejemplo, un problema de seguridad) para iniciar una excepción desde un constructor estático.

### <a name="finalizers"></a>Finalizadores
 Producir una excepción desde un finalizador hace que el CLR genere un error rápido, lo que anula el proceso. Por consiguiente, siempre debe evitarse la generación de excepciones en un finalizador.

### <a name="dispose-methods"></a>Métodos Dispose
 Un método <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> no debe producir una excepción. Dispose a menudo se llama como parte de la lógica de limpieza en una cláusula `finally`. Por consiguiente, iniciar explícitamente una excepción desde Dispose obliga al usuario a agregar el control de excepciones dentro de la cláusula `finally`.

 La ruta de acceso del código **Dispose (false)** nunca debe iniciar excepciones, ya que casi siempre se llama desde un finalizador.

### <a name="equality-operators--"></a>Operadores de igualdad (= =,! =)
 Al igual que los métodos Equals, los operadores de igualdad deben devolver `true` o `false` y no deben producir excepciones.

### <a name="implicit-cast-operators"></a>Operadores de conversión implícita
 Dado que el usuario a menudo no es consciente de que se ha llamado a un operador de conversión implícito, una excepción iniciada por el operador de conversión implícita es totalmente inesperada. Por lo tanto, no se debe producir ninguna excepción desde los operadores de conversión implícitos.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 En el caso de captadores de propiedades, cambie la lógica para que ya no tenga que producir una excepción, o bien cambie la propiedad a un método.

 En el caso de todos los demás tipos de método enumerados anteriormente, cambie la lógica para que ya no sea necesario producir una excepción.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si la infracción se debe a una declaración de excepción en lugar de a una excepción iniciada.

## <a name="related-rules"></a>Reglas relacionadas
 [CA2219: No producir excepciones en cláusulas de excepción](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)

## <a name="see-also"></a>Vea también
 [Advertencias de diseño](../code-quality/design-warnings.md)
