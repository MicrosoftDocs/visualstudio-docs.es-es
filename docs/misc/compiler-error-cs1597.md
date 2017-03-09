---
title: "Error del compilador CS1597 | Microsoft Docs"
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
  - "CS1597"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1597"
ms.assetid: 735e7cde-38de-4e15-96cc-ce75ffe34ff2
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1597
El punto y coma después del bloque de métodos o de descriptores de acceso no es válido  
  
 Los punto y coma no son necesarios \(ni están permitidos\) para finalizar un método o un bloque de descriptores de acceso.  
  
 El ejemplo siguiente genera la advertencia CS1597:  
  
```  
// CS1597.cs class TestClass { public static void Main() { };   // CS1597, remove semicolon }  
```