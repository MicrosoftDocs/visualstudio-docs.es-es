---
title: "No se pueden especificar modificadores de matriz en el nombre de par&#225;metros de expresi&#243;n lambda, solo en su tipo | Microsoft Docs"
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
  - "vbc36643"
  - "bc36643"
helpviewer_keywords: 
  - "BC36643"
ms.assetid: 34b6141b-6eab-4641-a3f4-53ef28c1792b
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se pueden especificar modificadores de matriz en el nombre de par&#225;metros de expresi&#243;n lambda, solo en su tipo
Los argumentos de matriz se pueden enviar a expresiones lambda, pero la declaración de parámetros debe incluir el tipo de elemento.  
  
```vb#  
' Not valid.  
' Dim arrayExample1 = Function(arrayPara()) 2  
  
' Valid.  
Dim arrayExample2 = Function(arrayPara() As Integer) arrayPara.Length > 0  
Dim arrayexample3 = Function(arrayPara As Integer()) arrayPara.Length > 0  
```  
  
 **Id. de error:** BC36643  
  
### Para corregir este error  
  
-   Especifique el tipo de los elementos del parámetro de la matriz.  
  
## Vea también  
 [Expresiones lambda](/dotnet/visual-basic/programming-guide/language-features/procedures/lambda-expressions)