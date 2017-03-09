---
title: "Error del compilador CS0819 | Microsoft Docs"
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
  - "CS0819"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0819"
ms.assetid: a5369e03-eb7d-4c88-b390-51304bd8d1ae
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0819
Las variables locales con tipo implícito no pueden tener varios declaradores.  
  
 El uso de varios declaradores está permitido en declaraciones de tipo explícito, pero no con variables de tipo implícito.  
  
### Para corregir este error  
  
1.  Declare y asigne un valor a cada variable local con tipo implícito en una línea independiente.  
  
## Ejemplo  
 El código siguiente genera el error CS0819:  
  
```  
// cs0819.cs class A { public static int Main() { var a = 3, b = 2; // CS0819 return -1; } }  
```  
  
## Vea también  
 [Variables locales con asignación implícita de tipos](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)