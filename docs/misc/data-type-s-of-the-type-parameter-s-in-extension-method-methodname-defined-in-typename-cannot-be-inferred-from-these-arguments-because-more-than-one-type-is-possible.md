---
title: "Los tipos de datos de los par&#225;metros de tipo del m&#233;todo de extensi&#243;n &#39;&lt;nombreDeM&#233;todo&gt;&#39; definido en &#39;nombreDeTipo&#39; no se pueden inferir de estos argumentos porque m&#225;s de un tipo es posible | Microsoft Docs"
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
  - "bc36655"
  - "vbc36652"
  - "vbc36655"
  - "bc36652"
helpviewer_keywords: 
  - "BC36655"
  - "BC36655"
ms.assetid: 49836f20-c877-4267-8bdc-6f6d108fb8c0
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los tipos de datos de los par&#225;metros de tipo del m&#233;todo de extensi&#243;n &#39;&lt;nombreDeM&#233;todo&gt;&#39; definido en &#39;nombreDeTipo&#39; no se pueden inferir de estos argumentos porque m&#225;s de un tipo es posible
Los tipos de datos de los parámetros de tipo del método de extensión '\<nombreDeMétodo\>' definido en 'nombreDeTipo' no se pueden inferir de estos argumentos porque más de un tipo es posible. Si se especifican los tipos de datos explícitamente, puede que se corrija este error.  
  
 Se intentó usar la inferencia de tipos para determinar el tipo o los tipos del parámetro o los parámetros de tipo en una llamada a un método de extensión genérico. El compilador encuentra más de un tipo de datos posible para uno o varios de los parámetros de tipo e informa de este error.  
  
> [!NOTE]
>  Cuando no es posible especificar argumentos \(por ejemplo, para operadores de consulta de expresiones de consulta\), el mensaje de error aparece sin la segunda oración.  
  
 El código siguiente muestra el error.  
  
```vb#  
Option Strict Off Imports System.Runtime.CompilerServices Module Module1 Sub Main() Dim caller As New Class1 '' Not valid. 'caller.targetExtension(1, "2") End Sub <Extension()> _ Sub targetExtension(Of T)(ByVal p0 As Class1, ByVal p1 As T, ByVal p2 As T) End Sub Class Class1 End Class End Module  
```  
  
 **Identificador de error:** BC36655 \(dentro de las consultas [!INCLUDE[vbteclinq](../misc/includes/vbteclinq_md.md)]\) y BC36652 \(fuera de las consultas\)  
  
### Para corregir este error  
  
-   Si el error aparece fuera de una consulta, intente especificar el tipo de datos del parámetro o los parámetros de tipo de forma explícita:  
  
    ```  
    caller.targetExtension(Of Integer)(1, "2") caller.targetExtension(Of String)(1, "2")  
    ```  
  
## Vea también  
 [métodos de extensión.](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Option Strict \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Procedimientos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)