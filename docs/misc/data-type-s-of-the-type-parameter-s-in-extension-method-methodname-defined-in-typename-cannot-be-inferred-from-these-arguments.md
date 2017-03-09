---
title: "Los tipos de datos de los par&#225;metros de tipo del m&#233;todo de extensi&#243;n &#39;&lt;nombreM&#233;todo&gt;&#39; definido en &#39;&lt;nombreTipo&gt;&#39; no se pueden inferir de estos argumentos. | Microsoft Docs"
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
  - "bc36649"
  - "vbc36646"
  - "bc36646"
  - "vbc36649"
helpviewer_keywords: 
  - "BC36649"
  - "BC36649"
ms.assetid: 55274b01-6d78-4950-861e-07d9273ef76e
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los tipos de datos de los par&#225;metros de tipo del m&#233;todo de extensi&#243;n &#39;&lt;nombreM&#233;todo&gt;&#39; definido en &#39;&lt;nombreTipo&gt;&#39; no se pueden inferir de estos argumentos.
Los tipos de datos de los parámetros de tipo del método de extensión '\<nombreMétodo\>' definido en '\<nombreTipo\>' no se pueden inferir de estos argumentos. Especificar los tipos de datos explícitamente puede corregir este error.  
  
 Se ha intentado usar la inferencia de tipo para determinar el tipo \(o tipos\) de datos del parámetro \(o parámetros\) de tipo al evaluar una llamada a un método de extensión genérico. Sin embargo, el compilador no es capaz de encontrar un tipo de datos para los parámetros de tipo en este método y notifica el error.  
  
> [!NOTE]
>  Al especificar argumentos no es una opción \(por ejemplo, para operadores de consulta en expresiones de consulta\), el mensaje de error aparece sin la segunda oración.  
  
 El código siguiente muestra el error.  
  
```vb#  
Module Module1 Sub Main() Dim classInstance As ClassExample '' Not valid. 'classInstance.GenericExtensionMethod("Hello", "World") End Sub <System.Runtime.CompilerServices.Extension()> _ Sub GenericExtensionMethod(Of T)(ByVal classEx As ClassExample, _ ByVal x As String, ByVal y As _ InterfaceExample(Of T)) End Sub End Module Interface InterfaceExample(Of T) End Interface Class ClassExample End Class  
```  
  
 **Identificador de error:** BC36649 y BC36646  
  
### Para corregir este error  
  
-   Es posible que pueda especificar un tipo de datos para el parámetro o parámetros de tipo en lugar de confiar en la inferencia de tipo.  
  
## Vea también  
 [Conversión de delegado flexible](/dotnet/visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion)   
 [métodos de extensión.](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Procedimientos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Conversiones de tipos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/type-conversions)