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
ms.openlocfilehash: f924e9530a7ee43ec2222366141c3af6be2efc29
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233610"
---
# <a name="ca1812-avoid-uninstantiated-internal-classes"></a>CA1812: Evitar las clases internas sin instancia

|||
|-|-|
|TypeName|AvoidUninstantiatedInternalClasses|
|Identificador de comprobación|CA1812|
|Categoría|Microsoft.Performance|
|Cambio importante|Poco problemático|

## <a name="cause"></a>Motivo

Nunca se crea una instancia de un tipo interno (nivel de ensamblado).

## <a name="rule-description"></a>Descripción de la regla

Esta regla intenta localizar una llamada a uno de los constructores del tipo y notifica una infracción si no se encuentra ninguna llamada.

Esta regla no examina los siguientes tipos:

- Tipos de valor

- Tipos abstractos

- Enumeraciones

- Delegados

- Tipos de matriz emitidos por el compilador

- Tipos de los que no se pueden crear instancias y [`static`](/dotnet/csharp/language-reference/keywords/static) que solo definen métodos ([ `Shared` en Visual Basic](/dotnet/visual-basic/language-reference/modifiers/shared)).

Si aplica al ensamblado que se está analizando, esta regla no marcará los <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute?displayProperty=fullName> tipos marcados como [`internal`](/dotnet/csharp/language-reference/keywords/internal) ([ `Friend` en Visual Basic](/dotnet/visual-basic/language-reference/modifiers/friend)) porque un campo puede ser utilizado por un ensamblado de confianza.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, quite el tipo o agregue el código que lo utiliza. Si el tipo solo `static` contiene métodos, agregue uno de los siguientes al tipo para evitar que el compilador emita un constructor de instancia público predeterminado:

- Modificador para `static` C# los tipos que tienen como destino .NET Framework 2,0 o posterior.

- Constructor privado para los tipos que tienen como destino .NET Framework versiones 1,0 y 1,1.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

Es seguro suprimir una advertencia de esta regla. Se recomienda suprimir esta advertencia en las situaciones siguientes:

- La clase se crea mediante métodos de reflexión enlazados en tiempo <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>de ejecución como.

- La clase la crea automáticamente el Runtime o ASP.NET. Algunos ejemplos de clases creadas automáticamente son aquellos que <xref:System.Configuration.IConfigurationSectionHandler?displayProperty=fullName> implementan <xref:System.Web.IHttpHandler?displayProperty=fullName>o.

- La clase se pasa como un parámetro de tipo que tiene una [ `new` restricción](/dotnet/csharp/language-reference/keywords/new-constraint). El siguiente ejemplo se marcará con la regla CA1812:

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

- [CA1811: Evitar código privado no llamado](../code-quality/ca1811-avoid-uncalled-private-code.md)
- [CA1801: Revisar los parámetros no usados](../code-quality/ca1801-review-unused-parameters.md)
- [CA1804: Quitar variables locales no usadas](../code-quality/ca1804-remove-unused-locals.md)