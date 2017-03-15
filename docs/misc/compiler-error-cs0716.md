---
title: "Error del compilador CS0716 | Microsoft Docs"
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
  - "CS0716"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0716"
ms.assetid: 806d25ef-f8a7-4c94-823e-e07904defcf4
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0716
No se puede convertir en el tipo estático 'type'  
  
 Este error se produce si el código usa una conversión en un tipo estático. Puesto que no es posible que un objeto sea una instancia de un tipo estático, la conversión en un tipo estático nunca puede ser significativa.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS0716:  
  
```  
// CS0716.cs public static class SC { static void F() { } } public class Test { public static void Main() { object o = new object(); System.Console.WriteLine((SC)o);  // CS0716 } }  
```