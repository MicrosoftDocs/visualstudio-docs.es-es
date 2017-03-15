---
title: "Error del compilador CS0815 | Microsoft Docs"
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
  - "CS0815"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0815"
ms.assetid: 8f055d34-9ee4-482e-9e79-8b3698c55cb4
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0815
No se puede asignar 'expresión' a una variable local con tipo implícito.  
  
 Una expresión que se usa como inicializador de una variable con tipo implícito debe tener un tipo. Dado que las expresiones de función anónima, las expresiones de grupo de métodos y la expresión literal NULL no tienen tipo, no son inicializadores adecuados. No se puede inicializar una variable con tipo implícito con un valor nulo en su declaración, aunque se puede asignar más adelante un valor nulo.  
  
### Para corregir este error  
  
1.  Proporcione un tipo explícito para la variable.  
  
## Ejemplo  
 El código siguiente genera el error CS0815:  
  
```  
// cs0815.cs class Test { public static int Main() { var d = s => -1; // CS0815 var e = (string s) => 0; // CS0815 var p = null;//CS0815 var del = delegate(string a) { return -1; };// CS0815 return -1; } }  
```  
  
## Vea también  
 [Variables locales con asignación implícita de tipos](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)