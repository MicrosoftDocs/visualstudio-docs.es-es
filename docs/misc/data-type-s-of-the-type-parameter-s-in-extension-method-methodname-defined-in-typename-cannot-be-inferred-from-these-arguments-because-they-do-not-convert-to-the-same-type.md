---
title: "Los tipos de datos de los par&#225;metros de tipo del m&#233;todo de extensi&#243;n &#39;&lt;methodname&gt;&#39; definido en &#39;typename&#39; no se pueden inferir de estos argumentos porque no se convierten en el mismo tipo | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36658"
  - "bc36661"
  - "vbc36661"
  - "bc36658"
helpviewer_keywords: 
  - "BC36661"
  - "BC36661"
ms.assetid: 0bff97fd-cbe9-4433-8192-6498c6fb5d04
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los tipos de datos de los par&#225;metros de tipo del m&#233;todo de extensi&#243;n &#39;&lt;methodname&gt;&#39; definido en &#39;typename&#39; no se pueden inferir de estos argumentos porque no se convierten en el mismo tipo
Los tipos de datos de los parámetros de tipo del método de extensión '\<methodname\>' definido en 'typename' no se pueden inferir de estos argumentos porque no se convierten en el mismo tipo. Especificar los tipos de datos explícitamente puede corregir este error.  
  
 Se ha intentado usar la inferencia de tipo para determinar el tipo \(o tipos\) de datos del parámetro \(o parámetros\) de tipo al evaluar una llamada a un método de extensión genérico. El compilador no pudo encontrar un tipo de datos que cumpla las restricciones de todos los argumentos. Por lo tanto, informa de este error.  
  
> [!NOTE]
>  Cuando no es posible especificar argumentos \(por ejemplo, para operadores de consulta de expresiones de consulta\), el mensaje de error aparece sin la segunda oración.  
  
 El código siguiente muestra el error.  
  
```vb#  
Option Strict Off Module Module3 Sub Main() Dim c1 As New Class1 '' Not valid. Integer and Date do not convert to the same type. 'c1.targetMethod(19, #3/4/2007#) End Sub <System.Runtime.CompilerServices.Extension()> _ Sub targetMethod(Of T)(ByVal p0 As Class1, ByVal p1 As T, ByVal p2 As T) End Sub Class Class1 End Class End Module  
```  
  
 **Identificador de error:** BC36661 y BC36658  
  
### Para corregir este error  
  
-   Puede convertir uno o más argumentos de manera explícita a un tipo compatible, como se muestra en el código siguiente:  
  
    ```  
    c1.targetMethod(19, #3/4/2007#.ToOADate)  
    ```  
  
-   Es posible que pueda especificar un tipo de datos para el parámetro de tipo o los parámetros en los que convertir los argumentos, como se muestra en el código siguiente:  
  
    ```  
    c1.targetMethod(Of String)(19, #3/4/2007#)  
    ```  
  
## Vea también  
 [métodos de extensión.](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Conversión de delegado flexible](/dotnet/visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion)   
 [Procedimientos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Funciones de conversión de tipos](/dotnet/visual-basic/language-reference/functions/type-conversion-functions)   
 [Conversiones implícitas y explícitas](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions)   
 [Conversiones de tipos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/type-conversions)