---
title: "Error del compilador CS0825 | Microsoft Docs"
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
  - "CS0825"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0825"
ms.assetid: 49393d23-ec5f-4b44-a3fd-7e0a95ac0edd
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0825
La palabra clave contextual 'var' solo puede aparecer en una declaración de variable local.  
  
 El establecimiento de tipos implícitos con la palabra clave `var` solo puede aplicarse a variables en el ámbito del método local.  
  
### Para corregir este error  
  
1.  Si la variable pertenece al ámbito de clase, asígnele un tipo explícito.  De lo contrario, muévala dentro del método donde se usará.  
  
## Ejemplo  
 El código siguiente genera el error CS0825 porque `var` se usa en un campo de clase:  
  
```  
// cs0825.cs class Test { private var myField; //CS0825 static int Main() { var a = 1; // var is OK here return -1; } }  
```  
  
## Vea también  
 [Variables locales con asignación implícita de tipos](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)