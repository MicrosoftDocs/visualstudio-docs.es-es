---
title: "Los tipos de datos de los par&#225;metros de tipo del m&#233;todo &#39;&lt;nombreM&#233;todo&gt;&#39; no se pueden inferir de estos argumentos porque no se convierten al mismo tipo. | Microsoft Docs"
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
  - "vbc36660"
  - "bc36660"
  - "vbc36657"
  - "bc36657"
helpviewer_keywords: 
  - "BC36660"
  - "BC36660"
ms.assetid: e80c5afd-e16d-4f03-bdf1-c79c4286114b
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los tipos de datos de los par&#225;metros de tipo del m&#233;todo &#39;&lt;nombreM&#233;todo&gt;&#39; no se pueden inferir de estos argumentos porque no se convierten al mismo tipo.
Los tipos de datos de los parámetros de tipo del método '\<nombreMétodo\>' no se pueden inferir de estos argumentos porque no se convierten al mismo tipo. Especificar los tipos de datos explícitamente puede corregir este error.  
  
 Se ha intentado usar la inferencia de tipo para determinar el tipo o tipos de datos del parámetro o parámetros de tipo al evaluar una llamada a un procedimiento genérico. El compilador no pudo encontrar un tipo de datos que cumpliera las restricciones de todos los argumentos. Por lo tanto, informa de este error.  
  
> [!NOTE]
>  Cuando no es posible especificar argumentos \(por ejemplo, para operadores de consulta de expresiones de consulta\), el mensaje de error aparece sin la segunda oración.  
  
 El código siguiente muestra el error.  
  
```vb#  
Option Strict Off Module Module1 Sub Main() '' Not valid. Integer and Date do not convert to the same type. 'targetMethod(19, #3/4/2007#) End Sub Sub targetMethod(Of T)(ByVal p1 As T, ByVal p2 As T) End Sub End Module  
```  
  
 **Identificador de error:** BC36660 y BC36657  
  
### Para corregir este error  
  
-   Puede convertir uno o más argumentos de manera explícita a un tipo compatible, como se muestra en el código siguiente:  
  
    ```  
    targetMethod(19, #3/4/2007#.ToOADate)  
    ```  
  
-   Puede especificar un tipo de datos para el parámetro o parámetros de tipo al que se convierten los argumentos, como se muestra en el código siguiente:  
  
    ```  
    targetMethod(Of String)(19, #3/4/2007#)  
    ```  
  
## Vea también  
 [Procedimientos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Funciones de conversión de tipos](/dotnet/visual-basic/language-reference/functions/type-conversion-functions)   
 [Conversiones implícitas y explícitas](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions)   
 [Conversiones de tipos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/type-conversions)