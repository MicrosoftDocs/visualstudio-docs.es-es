---
title: "Error del compilador CS0710 | Microsoft Docs"
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
  - "CS0710"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0710"
ms.assetid: 753a1a87-f5e5-4758-a960-515069a6c7b0
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0710
Las clases estáticas no pueden tener constructores de instancia  
  
 No pueden crearse instancias de una clase estática; por lo tanto, no se necesitan los constructores. Para evitar este error, quite todos los constructores de clases estáticas o, si realmente desea construir instancias, haga que la clase sea no estática.  
  
 El ejemplo siguiente genera la advertencia CS0710:  
  
```  
// CS0710.cs public static class C { public C()  // CS0710 { } public static void Main() { } }  
```