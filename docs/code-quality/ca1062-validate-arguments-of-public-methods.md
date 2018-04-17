---
title: 'CA1062: Validar argumentos de métodos públicos | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
- Validate arguments of public methods
helpviewer_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6a14017c63c9012609f91005378f44a5e4a8401e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="ca1062-validate-arguments-of-public-methods"></a>CA1062: Validar argumentos de métodos públicos

|||
|-|-|
|TypeName|ValidateArgumentsOfPublicMethods|
|Identificador de comprobación|CA1062|
|Categoría|Microsoft.Design|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo

Un método visible externamente desreferencia uno de sus argumentos de referencia sin comprobar si ese argumento es `null` (`Nothing` en Visual Basic).

## <a name="rule-description"></a>Descripción de la regla

Todos los argumentos de referencia que se pasan a métodos visibles externamente se deben comprobar para `null`. Si es necesario, producir una <xref:System.ArgumentNullException> cuando el argumento es `null`.

Si un método se puede llamar desde un ensamblado desconocido porque se ha declarado público o protegido, debe validar todos los parámetros del método. Si el método está diseñado para ser invocado únicamente por ensamblados conocidos, debería realizar el método interno y aplicar el <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributo al ensamblado que contiene el método.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, valide cada argumento de referencia con `null`.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

Puede suprimir una advertencia de esta regla si está seguro de que se ha validado el parámetro desreferenciado otra llamada de método en la función.

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

Constructores de copias que rellenan el campo o propiedades que son objetos de referencia también pueden infringir la regla CA1062. La infracción se produce porque el objeto copiado que se pasa al constructor de copias podría ser `null` (`Nothing` en Visual Basic). Para resolver la infracción, utilice un método estático (compartido en Visual Basic) para comprobar que el objeto copiado no es null.

En la siguiente `Person` ejemplo de la clase, el `other` objeto que se pasa a la `Person` constructor de copias podría ser `null`.

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

En el siguiente ejemplo revisado `Person` ejemplo, el `other` objeto que se pasa al constructor de copias se comprueba primero si hay valores null en la `PassThroughNonNull` método.

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