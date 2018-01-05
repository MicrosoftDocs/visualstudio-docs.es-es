---
title: "CA1062: Validar argumentos de métodos públicos | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
- Validate arguments of public methods
helpviewer_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
ms.assetid: db1f69ca-68f7-477e-94f3-d135cc5dfcbc
caps.latest.revision: "27"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: eb659fa8bfd18d8caf4a7473f6cd53809d0a126b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
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
 En [!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)], esta regla no detecta que se han pasado parámetros a otro método que realiza la validación.  

```csharp
public string Method(string value)
{
    EnsureNotNull(value);

    // Fires incorrectly    
    return value.ToString();
}

private void EnsureNotNull(string value)
{
    if (value == null)
        throw new ArgumentNullException("value");
}
```

```vb
Public Function Method(ByVal value As String) As String
    EnsureNotNull(value)

    ' Fires incorrectly    
    Return value.ToString()
End Function

Private Sub EnsureNotNull(ByVal value As String)
    If value Is Nothing Then
        Throw (New ArgumentNullException("value"))
    End If
End Sub
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