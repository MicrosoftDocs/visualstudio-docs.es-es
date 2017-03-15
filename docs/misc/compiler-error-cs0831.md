---
title: "Error del compilador CS0831 | Microsoft Docs"
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
  - "CS0831"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0831"
ms.assetid: f626a77d-3844-4438-954b-b8201e72b1b5
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0831
Un árbol de expresión no puede contener un acceso base.  
  
 Un acceso base significa realizar una llamada de función que, normalmente, sería una llamada de función virtual como una llamada de función no virtual en el método de clase base. Esto no está permitido en el árbol de expresión, pero puede invocar un método auxiliar en la clase que invoque el método de clase base.  
  
### Para corregir este error  
  
1.  Si debe acceder a un método de clase base de esta manera, cree un método auxiliar que llame a la clase base y haga que el árbol de expresión llame al método auxiliar. Esta técnica se muestra en el siguiente código.  
  
## Ejemplo  
 El siguiente ejemplo genera el error CS0831:  
  
```  
// cs0831.cs using System; using System.Linq; using System.Linq.Expressions; public class A { public virtual int BaseMethod() { return 1; } } public class C : A { public override int BaseMethod() { return 2; } public int Test(C c) { Expression<Func<int>> e = () => base.BaseMethod(); // CS0831 // Try the following line instead, // along with the BaseAccessHelper method. // Expression<Func<int>> e2 = () => BaseAccessHelper(); return 1; } // Uncomment to call from e2 expression above. // int BaseAccessHelper() // { //     return base.BaseMethod(); // } }   
```