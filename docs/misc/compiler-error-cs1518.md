---
title: "Error del compilador CS1518 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1518"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1518"
ms.assetid: 26e0870d-fe91-4c66-b3f8-ed2b074c964e
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1518
Se esperaba una clase, un delegado, una enumeración, una interfaz o un struct  
  
 Se encontró una declaración que no se admite en un [espacio de nombres](/dotnet/csharp/language-reference/keywords/namespace). Dentro de un espacio de nombres, el compilador solamente acepta clases, estructuras, enumeraciones, interfaces, espacios de nombres y delegados.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS1518:  
  
```  
// CS1518.cs namespace x { sealed class c1 {};      // OK namespace f2 {};         // OK sealed f3 {};            // CS1518 }  
```