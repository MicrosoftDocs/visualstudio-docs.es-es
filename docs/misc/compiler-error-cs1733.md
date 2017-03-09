---
title: "Error del compilador CS1733 | Microsoft Docs"
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
  - "CS1733"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1733"
ms.assetid: 2188aabe-404d-4a95-a11a-736dbd848508
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1733
Se esperaba una expresión.  
  
 Este error se produce siempre que el compilador espera una expresión en la línea donde se produjo el error. En el ejemplo siguiente, la coma final del inicializador indica al compilador que seguirá otra expresión.  
  
### Para corregir este error  
  
-   Proporcione la expresión que falta.  
  
-   Quite los tokens que hacen que el compilador espere una expresión.  
  
## Ejemplo  
 El siguiente ejemplo genera el error CS1733 debido a la coma final:  
  
```  
// cs1733.cs using System.Collections.Generic; public class Test { public static void Main() { List<int> list = new List<int>() {{ 1, 2, }};// CS1733 } }  
```