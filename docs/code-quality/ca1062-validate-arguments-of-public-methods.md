---
title: "CA1062: Validar argumentos de m&#233;todos p&#250;blicos | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1062"
  - "ValidateArgumentsOfPublicMethods"
  - "Validate arguments of public methods"
helpviewer_keywords: 
  - "CA1062"
  - "ValidateArgumentsOfPublicMethods"
ms.assetid: db1f69ca-68f7-477e-94f3-d135cc5dfcbc
caps.latest.revision: 27
caps.handback.revision: 27
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1062: Validar argumentos de m&#233;todos p&#250;blicos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ValidateArgumentsOfPublicMethods|  
|Identificador de comprobación|CA1062|  
|Categoría|Microsoft.Design|  
|Cambio problemático|No|  
  
## Motivo  
 Un método visible externamente desreferencia uno de sus argumentos de referencia sin comprobar si ese argumento es `null` \(`Nothing` en Visual Basic\).  
  
## Descripción de la regla  
 Todos los argumentos de referencia que se pasan a métodos visibles externamente se deben comprobar para ver si son `null`.  Si procede, inicie una excepción <xref:System.ArgumentNullException> cuando el argumento sea `null`.  
  
 Si se puede llamar a un método desde un ensamblado desconocido porque se declara público o protegido, debería validar todos los parámetros del método.  Si el método está diseñado para ser llamado solo por ensamblados conocidos, debería convertir el método en interno y aplicar el atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> al ensamblado que contiene el método.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, valide cada argumento de referencia con respecto a `null`.  
  
## Cuándo suprimir advertencias  
 Puede suprimir una advertencia de esta regla si está seguro de que otra llamada al método ha validado el parámetro desreferenciado en la función.  
  
## Ejemplo  
 El ejemplo siguiente muestra un método que infringe la regla y un método que la cumple.  
  
 [!code-cs[FxCop.Design.ValidateArguments#1](../code-quality/codesnippet/CSharp/ca1062-validate-arguments-of-public-methods_1.cs)]
 [!code-cs[FxCop.Design.ValidateArguments#1](../code-quality/codesnippet/CSharp/ca1062-validate-arguments-of-public-methods_1.cs)]
 [!code-vb[FxCop.Design.ValidateArguments#1](../code-quality/codesnippet/VisualBasic/ca1062-validate-arguments-of-public-methods_1.vb)]  
  
## Ejemplo  
 En [!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)], esta regla no detecta que se están pasando parámetros a otro método que realiza la validación.  
  
 [!code-cs[FxCop.Design.ValidateArguments#2](../code-quality/codesnippet/CSharp/ca1062-validate-arguments-of-public-methods_2.cs)]
 [!code-cs[FxCop.Design.ValidateArguments#2](../code-quality/codesnippet/CSharp/ca1062-validate-arguments-of-public-methods_2.cs)]
 [!code-vb[FxCop.Design.ValidateArguments#2](../code-quality/codesnippet/VisualBasic/ca1062-validate-arguments-of-public-methods_2.vb)]  
  
## Ejemplo  
 Los constructores de copias que rellenan el campo o las propiedades que son objetos de referencia también pueden infringir la regla CA1062.  La infracción se produce porque el objeto copiado que se pasa al constructor de copias podría ser `null` \(`Nothing` en Visual Basic\).  Para resolver la infracción, utilice un método static \(Shared en Visual Basic\) para comprobar que el objeto copiado no es null.  
  
 En el siguiente ejemplo de la clase `Person`, el objeto `other` que se pasa al constructor de copias `Person` podría ser `null`.  
  
```  
  
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
  
## Ejemplo  
 En el siguiente ejemplo revisado de `Person`, el objeto `other` que se pasa al constructor de copias se comprueba primero si es null en el método `PassThroughNonNull`.  
  
```  
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