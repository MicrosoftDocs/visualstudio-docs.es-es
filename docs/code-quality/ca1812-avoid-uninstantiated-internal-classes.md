---
title: 'CA1812: Evitar las clases internas sin instancia'
ms.date: 05/16/2019
ms.topic: reference
f1_keywords:
- CA1812
- AvoidUninstantiatedInternalClasses
helpviewer_keywords:
- AvoidUninstantiatedInternalClasses
- CA1812
ms.assetid: 1bb92a42-322a-44cc-98a8-8858212c1e1f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6946434708e38bde7f6efcfc8404da14f91b41ee
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/06/2019
ms.locfileid: "66744702"
---
# <a name="ca1812-avoid-uninstantiated-internal-classes"></a>CA1812: Evitar las clases internas sin instancia

|||
|-|-|
|TypeName|AvoidUninstantiatedInternalClasses|
|Identificador de comprobación|CA1812|
|Categoría|Microsoft.Performance|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo

Nunca se crea una instancia de un tipo interno de (nivel de ensamblado).

## <a name="rule-description"></a>Descripción de la regla

Esta regla intenta localizar una llamada a uno de los constructores del tipo e informa de una infracción si no se encuentra ninguna llamada.

Esta regla no examina los siguientes tipos:

- Tipos de valor

- Tipos abstractos

- Enumeraciones

- Delegados

- Tipos de matriz emitido por el compilador

- Tipos que no pueden crearse instancias, y que se definen sólo [ `static` ](/dotnet/csharp/language-reference/keywords/static) ([ `Shared` en Visual Basic](/dotnet/visual-basic/language-reference/modifiers/shared)) métodos.

Si aplica el <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute?displayProperty=fullName> al ensamblado que se está analizando, esta regla no marcará los tipos que están marcados como [ `internal` ](/dotnet/csharp/language-reference/keywords/internal) ([ `Friend` en Visual Basic](/dotnet/visual-basic/language-reference/modifiers/friend)) porque puede ser un campo usa un ensamblado de confianza.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, quite el tipo o agregue código que lo utiliza. Si el tipo contiene solo `static` agregar métodos, uno de los siguientes al tipo para evitar que el compilador emita un constructor de instancia público predeterminado:

- El `static` modificador C# tipos que tienen como destino .NET Framework 2.0 o posterior.

- Un constructor privado para los tipos que tienen como destino las versiones 1.0 y 1.1 de .NET Framework.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

Es seguro suprimir una advertencia de esta regla. Se recomienda que suprimir esta advertencia en las situaciones siguientes:

- Se crea la clase a través de métodos de reflexión en tiempo de ejecución, como <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>.

- La clase se crea automáticamente el tiempo de ejecución o ASP.NET. Algunos ejemplos de clases creadas automáticamente son aquellos que implementan <xref:System.Configuration.IConfigurationSectionHandler?displayProperty=fullName> o <xref:System.Web.IHttpHandler?displayProperty=fullName>.

- La clase se pasa como un parámetro de tipo que tiene un [ `new` restricción](/dotnet/csharp/language-reference/keywords/new-constraint). El ejemplo siguiente se marcarán por regla CA1812:

    ```csharp
    internal class MyClass
    {
        public DoSomething()
        {
        }
    }
    public class MyGeneric<T> where T : new()
    {
        public T Create()
        {
            return new T();
        }
    }

    MyGeneric<MyClass> mc = new MyGeneric<MyClass>();
    mc.Create();
    ```

## <a name="related-rules"></a>Reglas relacionadas

- [CA1811: Evitar código privado fuera de lugar](../code-quality/ca1811-avoid-uncalled-private-code.md)
- [CA1801: Revisar parámetros sin utilizar](../code-quality/ca1801-review-unused-parameters.md)
- [CA1804: Quitar a variables locales no utilizadas](../code-quality/ca1804-remove-unused-locals.md)