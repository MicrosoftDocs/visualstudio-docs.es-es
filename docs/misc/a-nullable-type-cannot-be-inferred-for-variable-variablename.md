---
title: "No se puede inferir un tipo que acepte valores Null para la variable &#39;&lt;variablename&gt;&#39;. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc36628"
  - "vbc36628"
helpviewer_keywords: 
  - "BC36628"
ms.assetid: 3e92ae19-6a19-4b0b-9dd9-fba31cdb85a6
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se puede inferir un tipo que acepte valores Null para la variable &#39;&lt;variablename&gt;&#39;.
No se puede inferir un tipo que acepte valores Null desde un tipo de referencia, como una matriz, una clase o un `String`. El valor desde el que se deduce el tipo de datos debe ser un tipo de valor. Este error se ilustra en el código siguiente:  
  
```vb#  
'' Not valid.   
'Dim arrList? = New ArrayList  
'Dim except? = New Exception  
'Dim obj? = New Object  
'Dim stringVar? = "Open the application."  
  
' Valid.  
Dim intVar? = 10  
```  
  
 **Identificador de error:** BC36628  
  
### Para corregir este error  
  
-   Quite la designación que acepta valores Null.  
  
## Vea también  
 [Tipos de valor que aceptan valores NULL](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)