---
title: "Advertencia del compilador (nivel 2) CS0469 | Microsoft Docs"
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
  - "CS0469"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0469"
ms.assetid: 773925ce-a8b2-4098-9ead-b96197442848
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 2) CS0469
El valor 'goto case' no se puede convertir implícitamente al tipo 'tipo'.  
  
 Al usar `goto case`, debe haber una conversión implícita del valor de goto case al tipo del conmutador.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS0469.  
  
```  
// CS0469.cs // compile with: /W:2 class Test { static void Main() { char c = (char)180; switch (c) { case (char)127: break; case (char)180: goto case 127;   // CS0469 // try the following line instead // goto case (char) 127; } } }  
```