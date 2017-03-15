---
title: "Error del compilador CS0411 | Microsoft Docs"
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
  - "CS0411"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0411"
ms.assetid: 290947c9-10d0-427e-99f2-bff20299d533
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0411
Los argumentos de tipo para el método 'método' no se pueden inferir a partir del uso. Pruebe a especificar los argumentos de tipo explícitamente.  
  
 Este error se produce si se llama a un método genérico sin proporcionar explícitamente los argumentos de tipo y el compilador no es capaz de deducir cuáles se pretende usar. Para evitar este error, agregue los argumentos de tipo que quiere usar entre corchetes angulares.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS0411:  
  
```  
// CS0411.cs class C { void G<T>() { } public static void Main() { G();  // CS0411 // Try this instead: // G<int>(); } }  
```  
  
## Ejemplo  
 Otros casos posibles en los que puede producirse este error incluyen cuando el parámetro es `null`, puesto que no tiene ninguna información de tipo:  
  
```  
// CS0411b.cs class C { public void F<T>(T t) where T : C { } public static void Main() { C c = new C(); c.F(null);  // CS0411 } }  
```