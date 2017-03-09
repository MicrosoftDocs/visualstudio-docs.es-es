---
title: "Error del compilador CS1643 | Microsoft Docs"
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
  - "CS1643"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1643"
ms.assetid: 521f352b-00fb-4d62-89be-44251db3cc5b
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1643
No todas las rutas de código devuelven un valor en el método de tipo 'tipo'.  
  
 Este error se produce si un cuerpo de delegado no tiene una instrucción return o tiene una instrucción return que el compilador no puede comprobar que se alcanzará. En el ejemplo siguiente, el compilador no intenta predecir el resultado de la condición de la bifurcación para comprobar que el bloque de método anónimo siempre devuelve un valor.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS1643:  
  
```  
// CS1643.cs delegate int MyDelegate(); class C { static void Main() { MyDelegate d = delegate {                 // CS1643 int i = 0; if (i == 0) return 1; }; } }  
```