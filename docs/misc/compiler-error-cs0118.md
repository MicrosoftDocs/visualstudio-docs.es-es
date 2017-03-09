---
title: "Error del compilador CS0118 | Microsoft Docs"
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
  - "CS0118"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0118"
ms.assetid: 9a612432-6e56-4e9b-9d8c-7d7b43f58c1a
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0118
'nombre\_construcción1' es 'construcción1', pero se usa como 'construcción2'  
  
 El compilador detectó una situación en la que se usó una construcción de forma errónea o se intentó una operación no permitida en una construcción. Algunos ejemplos comunes son los siguientes:  
  
-   Un intento de crear instancias de un espacio de nombres \(en lugar de una clase\)  
  
-   Un intento de llamar a un campo \(en lugar de un método\)  
  
-   Un intento de usar un tipo como una variable  
  
-   Un intento de usar un alias externo como un tipo  
  
 Para resolver este error, asegúrese de que la operación es válida para el tipo en el que se está ejecutando.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS0118.  
  
```  
// CS0118.cs // compile with: /target:library namespace MyNamespace { class MyClass { // MyNamespace not a class MyNamespace ix = new MyNamespace ();   // CS0118 } }  
```