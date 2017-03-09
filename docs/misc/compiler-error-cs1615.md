---
title: "Error del compilador CS1615 | Microsoft Docs"
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
  - "CS1615"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1615"
ms.assetid: 518bb07f-0e3a-4761-9931-66845eb5df1a
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1615
No se debe pasar el argumento 'número' con la palabra clave 'palabra clave'.  
  
 Se usó una de las palabras clave `ref` u **out** cuando la función no tomaba un parámetro `ref` u **out** para ese argumento. Para resolver este error, quite la palabra clave incorrecta y use la palabra clave adecuada que coincida con la declaración de función, si existe.  
  
 El ejemplo siguiente genera la advertencia CS1615:  
  
```  
// CS1615.cs class C { public void f(int i) {} public static void Main() { int i = 1; f(ref i);  // CS1615 } }  
```