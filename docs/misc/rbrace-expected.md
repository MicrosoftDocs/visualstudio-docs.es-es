---
title: "Se esperaba &#39;}&#39; | Microsoft Docs"
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
  - "vbc30370"
  - "bc30370"
helpviewer_keywords: 
  - "BC30370"
ms.assetid: a4ce9be9-fc5d-46ec-a217-c3428bd0b97e
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Se esperaba &#39;}&#39;
Una lista de restricciones o un inicializador de matriz no termina de manera válida.  
  
 Los valores de elemento con el que se va a inicializar una matriz deben incluirse entre llaves \(`{}`\).  
  
```  
Dim demoArray() As Integer = New Integer() {1, 2, 3}   
```  
  
 Del mismo modo, las restricciones de una lista de restricciones de un parámetro de tipo genérico deben incluirse entre llaves.  
  
```  
Public Class dictionaryMaker(Of t As {IComparable, IDisposable, New})   
```  
  
 **Identificador de error:** BC30370  
  
### Para corregir este error  
  
-   Use "}" al final de la lista de restricciones o del inicializador de matriz.  
  
## Vea también  
 [Matrices](/dotnet/visual-basic/programming-guide/language-features/arrays/index)   
 [Cómo: Inicializar una variable de matriz en Visual Basic](../Topic/How%20to:%20Initialize%20an%20Array%20Variable%20in%20Visual%20Basic.md)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)   
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)