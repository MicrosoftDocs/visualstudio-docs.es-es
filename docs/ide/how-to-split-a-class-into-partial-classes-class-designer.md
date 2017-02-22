---
title: "How to: Split a Class into Partial Classes (Class Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Class Designer, partial classes"
  - "partial classes, Class Designer"
ms.assetid: 6f6b0b30-3996-4569-9200-20482b3adf90
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# How to: Split a Class into Partial Classes (Class Designer)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede dividir una declaración de clase o estructura en varias declaraciones utilizando la palabra clave `Partial` en Visual Basic o la palabra clave `partial` en Visual C\#.  Puede utilizar tantas declaraciones parciales como desee, en tantos archivos de código fuente diferentes como sea necesario o en un solo archivo de este tipo.  Sin embargo, todas las declaraciones deben estar en el mismo ensamblado y el mismo espacio de nombres.  
  
 Las clases parciales son útiles en diversas situaciones.  Por ejemplo, cuando se trabaja en proyectos grandes, separar una clase en más de un archivo permite que más de un programador trabaje en ésta al mismo tiempo.  Al trabajar con código generado por Visual Studio, puede cambiar la clase sin tener que volver a crear el archivo de código fuente.  \(Entre los ejemplos de código que genera Visual Studio se incluyen el código de formularios Windows Forms y el código contenedor de servicios Web.\) Así, puede crear código que utilice clases generadas automáticamente sin tener que modificar el archivo creado por Visual Studio.  
  
 Hay dos tipos de métodos parciales.  Tanto en Visual C\# como Visual Basic se llaman declaración e implementación.  
  
 El Diseñador de clases admite clases y métodos parciales.  La forma de tipo en el diagrama de clases hace referencia a una ubicación de declaración única para la clase parcial.  Si la clase parcial está definida en varios archivos, puede especificar qué ubicación de declaración utilizará el Diseñador de clases estableciendo la propiedad **Ubicación de nuevos miembros** en la ventana **Propiedades**.  Es decir, al hacer doble clic en una forma de clase, el Diseñador de clases se dirige al archivo de código fuente que contiene la declaración de clase identificada por la propiedad **Ubicación de nuevos miembros**.  Al hacer doble clic en un método parcial de una forma de clase, el Diseñador de clases se dirige a la declaración del método parcial.  Asimismo, en la ventana **Propiedades**, la propiedad **Nombre de archivo** hace referencia a la ubicación de la declaración.  Para las clases parciales, **Nombre de archivo** muestra todos los archivos que contienen código de declaración e implementación para esa clase.  Sin embargo, para los métodos parciales, **Nombre de archivo** solamente muestra el archivo que contiene la declaración de método parcial.  
  
 En los ejemplos siguientes se divide la definición de la clase `Employee` en dos declaraciones, cada una de las cuales define un procedimiento diferente.  Las dos definiciones parciales de los ejemplos podrían estar en un archivo de código fuente o en dos archivos distintos de este tipo.  
  
> [!NOTE]
>  Visual Basic utiliza definiciones de clase parciales para separar el código generado por Visual Studio del código creado por el usuario.  El código se separa en archivos de código fuente discretos.  Por ejemplo, el **Diseñador de Windows Forms** define clases parciales para los controles, como `Form`.  No debería modificar el código generado de estos controles.  
  
 Para obtener más información sobre los tipos parciales en Visual Basic, vea [Partial](/dotnet/visual-basic/language-reference/modifiers/partial).  
  
## Ejemplo  
 Para dividir una definición de clase en Visual Basic, utilice la palabra clave `Partial`, como se muestra en el ejemplo siguiente.  
  
```vb#  
' First part of class definition.  
Partial Public Class Employee  
    Public Sub CalculateWorkHours()  
    End Sub  
End Class  
  
' Second part of class definition.  
Partial Public Class Employee  
    Public Sub CalculateTaxes()  
    End Sub  
End Class  
```  
  
## Ejemplo  
 Para dividir una definición de clase en Visual C\#, utilice la palabra clave `partial`, como se muestra en el ejemplo siguiente.  
  
```c#  
// First part of class definition.  
public partial class Employee  
{  
    public void CalculateWorkHours()  
    {  
    }  
}  
  
// Second part of class definition.  
public partial class Employee  
{  
    public void CalculateTaxes()  
    {  
    }  
}  
```  
  
## Vea también  
 [Clases y métodos parciales](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)   
 [partial \(Tipos\)](/dotnet/csharp/language-reference/keywords/partial-type)   
 [Método parcial \(Referencia de C\#\)](/dotnet/csharp/language-reference/keywords/partial-method)   
 [Partial](/dotnet/visual-basic/language-reference/modifiers/partial)