---
title: "CA1024: Utilizar las propiedades donde corresponda | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UsePropertiesWhereAppropriate"
  - "CA1024"
helpviewer_keywords: 
  - "CA1024"
  - "UsePropertiesWhereAppropriate"
ms.assetid: 3a04f765-af7c-4872-87ad-9cc29e8e657f
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 21
---
# CA1024: Utilizar las propiedades donde corresponda
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UsePropertiesWhereAppropriate|  
|Identificador de comprobación|CA1024|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un método público o protegido tiene un nombre que comienza por `Get`, no toma ningún parámetro y devuelve un valor que no es una matriz.  
  
## Descripción de la regla  
 En la mayoría de los casos, las propiedades representan datos y los métodos realizan acciones.  Se tiene acceso a las propiedades igual que a los campos, que los hacen más sencillos de utilizar.  Un método es un buen candidato para convertirse en una propiedad si una de estas condiciones está presente:  
  
-   No toma argumentos y devuelve la información de estado de un objeto.  
  
-   Acepta un argumento único para establecer alguna parte del estado de un objeto.  
  
 Las propiedades deberían comportarse como si fueran campos; si el método no puede, no se debería cambiar a una propiedad.  Los métodos son mejores que las propiedades en las siguientes situaciones:  
  
-   El método realiza una operación que exige mucho tiempo.  El método es perceptiblemente más lento que el tiempo necesario para establecer u obtener el valor de un campo.  
  
-   El método realiza una conversión.  Al tener acceso a un campo, no se devuelve una versión convertida de los datos que almacena.  
  
-   El método Get tiene un efecto secundario notable.  Al recuperar el valor de un campo, no se genera ningún efecto secundario.  
  
-   El orden de ejecución es importante.  Al establecer el valor de un campo no se confía en que se produzcan otras operaciones.  
  
-   Llamar al método dos veces seguidas da lugar a resultados distintos.  
  
-   El método es estático pero devuelve un objeto que puede ser cambiado por el llamador.  Recuperar el valor de un campo no permite al llamador cambiar los datos almacenados por el campo.  
  
-   El método devuelve una matriz.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, cambie el método a una propiedad.  
  
## Cuándo suprimir advertencias  
 Suprima una advertencia de esta regla si el método cumple por lo menos uno de los criterios previamente mostrados.  
  
## Controlar la expansión de propiedades en el depurador  
 Una razón por la que los programadores evitan utilizar una propiedad es porque no desean que el depurador la expanda automáticamente.  Por ejemplo, es posible que la propiedad conlleve la asignación de un objeto grande o una llamada a P\/Invoke, pero realmente no tendría efectos secundarios apreciables.  
  
 Puede evitar que el depurador expanda automáticamente las propiedades aplicando <xref:System.Diagnostics.DebuggerBrowsableAttribute?displayProperty=fullName>.  En el ejemplo siguiente se muestra la aplicación de este atributo a una propiedad de instancia.  
  
```vb  
Imports System   
Imports System.Diagnostics   
  
Namespace Microsoft.Samples   
  
    Public Class TestClass   
  
        ' [...]   
  
        <DebuggerBrowsable(DebuggerBrowsableState.Never)> _   
        Public ReadOnly Property LargeObject() As LargeObject   
            Get   
                ' Allocate large object   
                ' [...]   
            End Get   
        End Property   
  
    End Class   
  
End Namespace  
```  
  
```c#  
  
        using System;   
using System.Diagnostics;   
  
namespace Microsoft.Samples   
{   
    public class TestClass   
    {   
        // [...]   
  
        [DebuggerBrowsable(DebuggerBrowsableState.Never)]   
        public LargeObject LargeObject   
        {   
            get   
            {   
                // Allocate large object   
                // [...]   
  
        }  
    }  
}  
```  
  
## Ejemplo  
 El ejemplo siguiente contiene varios métodos que se deberían convertirse en propiedades, y varios que no deben porque no se comportan como campos.  
  
 [!code-cs[FxCop.Design.MethodsProperties#1](../code-quality/codesnippet/CSharp/ca1024-use-properties-where-appropriate_1.cs)]