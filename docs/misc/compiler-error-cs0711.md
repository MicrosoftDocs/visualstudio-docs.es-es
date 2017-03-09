---
title: "Error del compilador CS0711 | Microsoft Docs"
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
  - "CS0711"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0711"
ms.assetid: 3a5a6d90-e15d-4808-a7a6-c85fd011a0d0
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0711
Las clases estáticas no pueden contener destructores  
  
 No pueden crearse instancias de una clase estática; por lo tanto, no se necesitan los constructores o destructores. Para evitar este error, quite todos los destructores de clases estáticas o, si realmente desea construir o destruir instancias, haga que la clase sea no estática.  
  
 El ejemplo siguiente genera la advertencia CS0711:  
  
```  
// CS0711.cs public static class C { ~C()  // CS0711 { } public static void Main() { } }  
```