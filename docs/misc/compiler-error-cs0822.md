---
title: "Error del compilador CS0822 | Microsoft Docs"
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
  - "CS0822"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0822"
ms.assetid: 519091be-2332-4df4-acd9-e3b633966b3d
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0822
Las variables locales con tipo implícito no pueden ser const.  
  
 Las variables locales con tipo implícito solo son necesarias para almacenar tipos anónimos. En todos los demás casos son simplemente por comodidad. Si el valor de la variable nunca cambia, puede darle un tipo explícito. Si se intenta usar el modificador `readonly` con una variable local con tipo implícito, generará CS0106.  
  
### Para corregir este error  
  
1.  Si necesita que la variable sea constante o `readonly`, puede darle un tipo explícito.  
  
## Ejemplo  
 El código siguiente genera CS0822:  
  
```  
// cs0822.cs class A { public static int Main() { const var x = 0; // CS0822.cs return -1; } }  
```  
  
## Vea también  
 [Variables locales con asignación implícita de tipos](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)