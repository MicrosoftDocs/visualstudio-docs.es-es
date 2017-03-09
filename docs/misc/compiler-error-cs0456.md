---
title: "Error del compilador CS0456 | Microsoft Docs"
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
  - "CS0456"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0456"
ms.assetid: d714ec06-a7f4-405e-bf32-423696848319
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0456
El parámetro de tipo 'Type Parameter Name 1' tiene la restricción 'struct'; por tanto, 'Type Parameter Name 1' no se puede utilizar como restricción para 'Type Parameter Name 2'  
  
 Las restricciones de tipo de valor están selladas implícitamente, por lo que no se pueden usar las restricciones como restricciones en un segundo parámetro de tipo. Esto es porque los tipos de valor no se puede invalidar. Para resolver este error, coloque una restricción de tipo de valor directamente en el segundo parámetro de tipo, en lugar de hacerlo indirectamente por medio del primer parámetro de tipo.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS0456.  
  
```  
// CS0456.cs // compile with: /target:library public class GenericsErrors { public class G5<T> where T : struct { public class N<U> where U : T {}   // CS0456 public class N2<U> where U : struct {}   // OK } }  
```