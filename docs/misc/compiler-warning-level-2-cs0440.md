---
title: "Advertencia del compilador (nivel 2) CS0440 | Microsoft Docs"
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
  - "CS0440"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0440"
ms.assetid: ade6761f-4d7d-42bc-a0c5-bbb1b987a1aa
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 2) CS0440
No es aconsejable definir ningún alias denominado 'global' porque 'global::' siempre hace referencia al espacio de nombres global y no a un alias  
  
 Esta advertencia se emite cuando se define un alias denominado global.  
  
## Ejemplo  
 El ejemplo siguiente genera el error CS0440:  
  
```  
// CS0440.cs // Compile with: /W:1 using global = MyClass;   // CS0440 class MyClass { static void Main() { // Note how global refers to the global namespace // even though it is redefined above. global::System.Console.WriteLine(); } }  
```