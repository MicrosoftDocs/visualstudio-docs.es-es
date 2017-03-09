---
title: "Error del compilador CS0694 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0694"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0694"
ms.assetid: 048615e4-4599-4726-b5db-55322ccc936f
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0694
El parámetro de tipo 'identifier' tiene el mismo nombre que el tipo contenedor o el método  
  
 Debe utilizar un nombre diferente para el parámetro de tipo, ya que el nombre del parámetro de tipo no puede coincidir con el nombre del método o el tipo que contiene el parámetro de tipo.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS0694.  
  
```  
// CS0694.cs // compile with: /target:library class C<C> {}   // CS0694  
```  
  
## Ejemplo  
 Además del caso anterior, donde se incluye una clase genérica, este error puede producirse con un método:  
  
```  
// CS0694_2.cs // compile with: /target:library class A { public void F<F>(F arg);   // CS0694 }  
```