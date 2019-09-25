---
title: 'CA1062: Validar argumentos de métodos públicos'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
- Validate arguments of public methods
helpviewer_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8106a4c0244cbd79e88a2bdc50e04ea74627dab4
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235334"
---
# <a name="ca1062-validate-arguments-of-public-methods"></a>CA1062: Validar argumentos de métodos públicos

|||
|-|-|
|TypeName|ValidateArgumentsOfPublicMethods|
|Identificador de comprobación|CA1062|
|Categoría|Microsoft.Design|
|Cambio importante|Poco problemático|

## <a name="cause"></a>Motivo

Un método visible externamente desreferencia uno de sus argumentos de referencia sin comprobar si ese argumento es `null` (`Nothing` en Visual Basic).

## <a name="rule-description"></a>Descripción de la regla

Todos los argumentos de referencia que se pasan a métodos visibles externamente deben comprobarse `null`. Si es necesario, produce <xref:System.ArgumentNullException> una excepción cuando el `null`argumento es.

Si se puede llamar a un método desde un ensamblado desconocido porque se ha declarado público o protegido, debe validar todos los parámetros del método. Si el método está diseñado para que solo lo llamen los ensamblados conocidos, debe hacer que el método sea <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> interno y aplicar el atributo al ensamblado que contiene el método.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, valide cada argumento de `null`referencia en.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

Puede suprimir una advertencia de esta regla si está seguro de que el parámetro desreferenciado se ha validado mediante otra llamada al método en la función.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra un método que infringe la regla y un método que cumple la regla.

```csharp
using System;

namespace DesignLibrary
{
    public class Test
    {
        // This method violates the rule.
        public void DoNotValidate(string input)
        {
            if (input.Length != 0)
            {
                Console.WriteLine(input);
            }
        }

        // This method satisfies the rule.
        public void Validate(string input)
        {
            if (input == null)
            {
                throw new ArgumentNullException("input");
            }
            if (input.Length != 0)
            {
                Console.WriteLine(input);
            }
        }
    }
}
```

```vb
Imports System

Namespace DesignLibrary

    Public Class Test

        ' This method violates the rule.
        Sub DoNotValidate(ByVal input As String)

            If input.Length <> 0 Then
                Console.WriteLine(input)
            End If

        End Sub

        ' This method satisfies the rule.
        Sub Validate(ByVal input As String)

            If input Is Nothing Then
                Throw New ArgumentNullException("input")
            End If

            If input.Length <> 0 Then
                Console.WriteLine(input)
            End If

        End Sub

    End Class

End Namespace
```

## <a name="example"></a>Ejemplo

Los constructores de copia que rellenan el campo o las propiedades que son objetos de referencia también pueden infringir la regla CA1062. La infracción se produce porque el objeto copiado que se pasa al constructor de `null` copias`Nothing` podría ser (en Visual Basic). Para resolver la infracción, use un método estático (compartido en Visual Basic) para comprobar que el objeto copiado no es NULL.

En el ejemplo `Person` de clase siguiente, `other` el objeto que se pasa al `Person` constructor de copias podría `null`ser.

```csharp
public class Person
{
    public string Name { get; private set; }
    public int Age { get; private set; }

    public Person(string name, int age)
    {
        Name = name;
        Age = age;
    }

    // Copy constructor CA1062 fires because other is dereferenced
    // without being checked for null
    public Person(Person other)
        : this(other.Name, other.Age)
    {
    }
}
```

## <a name="example"></a>Ejemplo

En el siguiente ejemplo `Person` revisado, el `other` objeto que se pasa al constructor de copias se comprueba primero si es null en `PassThroughNonNull` el método.

```csharp
public class Person
{
    public string Name { get; private set; }
    public int Age { get; private set; }

    public Person(string name, int age)
    {
        Name = name;
        Age = age;
    }

    // Copy constructor
    public Person(Person other)
        : this(PassThroughNonNull(other).Name,
          PassThroughNonNull(other).Age)
    {
    }

    // Null check method
    private static Person PassThroughNonNull(Person person)
    {
        if (person == null)
            throw new ArgumentNullException("person");
        return person;
    }
}
```