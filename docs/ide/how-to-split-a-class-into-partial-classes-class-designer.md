---
title: "Cómo: Dividir una clase en clases parciales (Diseñador de clases) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Class Designer, partial classes
- partial classes, Class Designer
ms.assetid: 6f6b0b30-3996-4569-9200-20482b3adf90
caps.latest.revision: 10
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 63aad78bdc7df685ca3a73ec16a9cbc87b78151f
ms.openlocfilehash: 9d74565f8e7e5b89e1716e9e2d88e2e18e077124
ms.contentlocale: es-es
ms.lasthandoff: 07/14/2017

---
# <a name="how-to-split-a-class-into-partial-classes-class-designer"></a>Cómo: Dividir una clase en clases parciales (Diseñador de clases)
Puede dividir la declaración de una clase o estructura entre varias declaraciones mediante la palabra clave `Partial` en Visual Basic o la palabra clave `partial` en Visual C#. Puede usar todas las declaraciones parciales que quiera en todos los archivos de código fuente que quiera o en un archivo de código fuente, pero todas las declaraciones deben estar en el mismo ensamblado y en el mismo espacio de nombres.  
  
 Las clases parciales son útiles en varias situaciones. Por ejemplo, cuando trabaja en proyectos grandes, separar una clase en más de un archivo permite que pueda trabajar en ella más de un programador. Cuando trabaja con código generado por Visual Studio, puede cambiar la clase sin tener que volver a crear el archivo de origen. (Los ejemplos de código generados por Visual Studio incluyen código de contenedor de Windows Forms y servicio Web). Así, puede crear código que use clases generadas automáticamente sin necesidad de modificar el archivo creado por Visual Studio.  
  
 Hay dos tipos de métodos parciales. En Visual C#, se denominan declarativo y de implementación. En Visual Basic, se denominan de declaración e implementación.  
  
 El diseñador de clases admite clases y métodos parciales. La forma de tipo en el diagrama de clases hace referencia a una ubicación de declaración única para la clase parcial. Si se define la clase parcial en varios archivos, puede especificar la ubicación de la declaración que va a usar el diseñador de clases estableciendo la propiedad **Ubicación de nuevos miembros** en la ventana **Propiedades**. Es decir, al hacer doble clic en una forma de clase, el diseñador de clases entra en el archivo de origen que contiene la declaración de clase identificada por la propiedad **Ubicación de nuevos miembros**. Cuando hace doble clic en un método parcial de una forma de clase, el diseñador de clases se va a la declaración de método parcial. Asimismo, en la ventana **Propiedades**, la propiedad **Nombre de archivo** hace referencia a la ubicación de la declaración. Para las clases parciales, **Nombre de archivo** enumera todos los archivos que contienen código de declaración e implementación de esa clase. Sin embargo, para los métodos parciales, **Nombre de archivo** muestra solo el archivo que contiene la declaración de método parcial.  
  
 Los siguientes ejemplos dividen la definición de la clase `Employee` en dos declaraciones, cada una de las cuales define otro procedimiento. Las dos definiciones parciales de los ejemplos podrían estar en un archivo de origen o en dos archivos distintos.  
  
> [!NOTE]
>  Visual Basic usa definiciones de clase parcial para separar el código generado por Visual Studio del código creado por el usuario. El código se divide en archivos de código fuente distintos. Por ejemplo, el **Diseñador de Windows Forms`Form` define clases parciales para controles como** . No debe modificar el código generado en estos controles.  
  
 Para obtener más información sobre los tipos parciales en Visual Basic, vea [Partial](/dotnet/visual-basic/language-reference/modifiers/partial).  
  
## <a name="example"></a>Ejemplo  
 Para dividir una definición de clase en Visual Basic, use la palabra clave `Partial`, como se muestra en el ejemplo siguiente.  
  
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
  
## <a name="example"></a>Ejemplo  
 Para dividir una definición de clase en Visual C#, use la palabra clave `partial`, como se muestra en el ejemplo siguiente.  
  
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
  
## <a name="see-also"></a>Vea también  
 [Clases y métodos parciales](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)   
 [partial (tipo)](/dotnet/csharp/language-reference/keywords/partial-type)   
 [partial (método, referencia de C#)](/dotnet/csharp/language-reference/keywords/partial-method)   
 [Partial](/dotnet/visual-basic/language-reference/modifiers/partial)
