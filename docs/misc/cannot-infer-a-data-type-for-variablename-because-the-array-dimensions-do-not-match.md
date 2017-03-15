---
title: "No se puede inferir un tipo de datos para &#39;&lt;nombreVariable&gt;&#39; porque las dimensiones de la matriz no coinciden. | Microsoft Docs"
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
  - "bc36909"
  - "vbc36909"
helpviewer_keywords: 
  - "BC36909"
ms.assetid: e41fec81-efec-4395-a0a5-d81906a2d4f1
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se puede inferir un tipo de datos para &#39;&lt;nombreVariable&gt;&#39; porque las dimensiones de la matriz no coinciden.
Si las dimensiones usadas para inicializar una matriz no coinciden con las dimensiones de la declaración, el compilador no puede inferir un tipo de datos para la matriz. Por ejemplo, el código siguiente causa este error.  
  
```vb#  
' Valid. exampleArray1 is a one-dimensional array of integers. Dim exampleArray1() = New Integer() {1, 2, 3} ' Not valid. 'Dim exampleArray2(,) = New Integer() {1, 2, 3} 'Dim exampleArray3(,) = New Integer() {}  
```  
  
 **Identificador de error:** BC36909  
  
## Vea también  
 [Inferencia de tipo de variable local](/dotnet/visual-basic/programming-guide/language-features/variables/local-type-inference)   
 [NO ESTÁ EN LA COMPILACIÓN: Cómo: Inicializar una matriz multidimensional](http://msdn.microsoft.com/es-es/502dcf8b-d86c-46f1-ad7d-3ce809645774)