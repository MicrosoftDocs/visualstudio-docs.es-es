---
title: "Error del compilador CS0623 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0623"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0623"
ms.assetid: c9fd6888-b9c5-48bf-b25b-2fae1446ad24
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0623
Los inicializadores de matriz solo se pueden utilizar en un inicializador de campo o variable. Pruebe a utilizar una expresión new en su lugar.  
  
 Se intentó inicializar una matriz con un inicializador de matriz en un contexto donde no está permitido.  
  
## Ejemplo  
 El ejemplo siguiente genera el error CS0623 porque el compilador interpreta \\{4\\} como un inicializador de matriz incrustado dentro del inicializador de la matriz externa:  
  
```  
//cs0632.cs using System; class X { public int[] x = { 2, 3, {4}}; //CS0623 }  
```  
  
## Vea también  
 [Matrices](/dotnet/csharp/programming-guide/arrays/index)