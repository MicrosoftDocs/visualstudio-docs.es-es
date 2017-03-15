---
title: "Error del compilador CS1100 | Microsoft Docs"
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
  - "CS1100"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1100"
ms.assetid: ea233371-36b6-49ae-a98c-a00ee3b79e53
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1100
El método 'nombre' tiene un modificador de parámetro 'this' que no está en el primer parámetro.  
  
 El modificador `this` solo se permite en el primer parámetro de un método, e indica al compilador que el método es un método de extensión.  
  
### Para corregir este error  
  
1.  Quite el modificador `this` de todos los parámetros del método excepto del primero.  
  
## Ejemplo  
 El código siguiente genera CS1100 porque un parámetro `this`  está modificando el segundo parámetro:  
  
```  
// cs1100.cs static class Test { static void ExtMethod(int i, this Test c) // CS1100 { } }  
```  
  
## Vea también  
 [Métodos de extensión](/dotnet/csharp/programming-guide/classes-and-structs/extension-methods)