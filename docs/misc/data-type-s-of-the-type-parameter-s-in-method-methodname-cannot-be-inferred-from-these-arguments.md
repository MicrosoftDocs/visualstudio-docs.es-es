---
title: "Los tipos de datos de los par&#225;metros de tipo del m&#233;todo &#39;&lt;methodname&gt;&#39; no se pueden deducir a partir de estos argumentos | Microsoft Docs"
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
  - "vbc36648"
  - "bc36645"
  - "bc36648"
  - "vbc36645"
helpviewer_keywords: 
  - "BC36648"
  - "BC36645"
ms.assetid: cc8c67bb-6cbb-4d7c-ba26-fe1d38908434
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los tipos de datos de los par&#225;metros de tipo del m&#233;todo &#39;&lt;methodname&gt;&#39; no se pueden deducir a partir de estos argumentos
Los tipos de datos de los parámetros de tipo del método '\<methodname\>' no se pueden deducir a partir de estos argumentos. Si se especifican los tipos de datos explícitamente, puede que se corrija este error.  
  
 Se ha intentado usar la inferencia de tipos para determinar el tipo \(o los tipos\) de datos del parámetro \(o los parámetros\) de tipo al evaluar una llamada a un procedimiento genérico. Sin embargo, el compilador no encuentra un tipo de datos para los parámetros de tipo en este método y notifica el error.  
  
> [!NOTE]
>  Cuando no es posible especificar argumentos \(por ejemplo, para operadores de consulta de expresiones de consulta\), el mensaje de error aparece sin la segunda oración.  
  
 Por ejemplo, el código siguiente muestra el error.  
  
```vb#  
Module Module1 Sub Main() '' Not valid. 'GenericMethod("Hello", "World") End Sub Sub GenericMethod(Of T)(ByVal x As String, ByVal y As _ InterfaceExample(Of T)) End Sub End Module Interface InterfaceExample(Of T) End Interface  
```  
  
 **Id. de error:** BC36648 y BC36645  
  
### Para corregir este error  
  
-   Es posible que pueda especificar un tipo de datos para el parámetro o los parámetros de tipo en lugar de confiar en la inferencia de tipos.  
  
## Vea también  
 [Procedimientos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Conversiones de tipos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/type-conversions)