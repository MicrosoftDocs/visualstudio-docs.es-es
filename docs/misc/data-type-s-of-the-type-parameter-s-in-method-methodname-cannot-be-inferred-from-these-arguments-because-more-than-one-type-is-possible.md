---
title: "Los tipos de datos de los par&#225;metros de tipo del m&#233;todo &#39;&lt;methodname&gt;&#39; no se pueden inferir de estos argumentos porque hay m&#225;s de un tipo posible | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc36651"
  - "bc36654"
  - "vbc36651"
  - "vbc36654"
helpviewer_keywords: 
  - "BC36651"
  - "BC36651"
ms.assetid: d4bf408c-ca1f-44ad-855a-3df898de60c6
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los tipos de datos de los par&#225;metros de tipo del m&#233;todo &#39;&lt;methodname&gt;&#39; no se pueden inferir de estos argumentos porque hay m&#225;s de un tipo posible
Los tipos de datos de los parámetros de tipo del método '\<methodname\>' no se pueden inferir de estos argumentos porque hay más de un tipo posible. Si se especifican los tipos de datos explícitamente, puede que se corrija este error.  
  
 Se ha intentado usar la inferencia de tipos para determinar el tipo o los tipos de datos del parámetro o los parámetros de tipo en una llamada a un procedimiento genérico. El compilador encuentra más de un tipo de datos para uno o varios de los parámetros de tipo e informa de este error.  
  
> [!NOTE]
>  Cuando no es posible especificar argumentos \(por ejemplo, para operadores de consulta de expresiones de consulta\), el mensaje de error aparece sin la segunda oración.  
  
 El código siguiente muestra el error.  
  
```vb#  
Option Strict Off Module Module1 Sub Main() '' Not valid. 'targetMethod(1, "2") End Sub Sub targetMethod(Of T)(ByVal p1 As T, ByVal p2 As T) End Sub End Module  
```  
  
 **Identificador de error:** BC36654 \(dentro de consultas [!INCLUDE[vbteclinq](../misc/includes/vbteclinq_md.md)]\) y BC36651 \(fuera de las consultas\)  
  
### Para corregir este error  
  
-   Si aparece el error fuera de una consulta, pruebe especificando el tipo de datos del parámetro de tipo explícitamente:  
  
    ```  
    targetMethod(Of Integer)(1, "2")  
    ```  
  
## Vea también  
 [Option Strict \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Procedimientos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)