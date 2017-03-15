---
title: "Error del compilador CS1007 | Microsoft Docs"
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
  - "CS1007"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1007"
ms.assetid: b56ee2c6-8e79-4b9b-8c59-194bdb22bc3e
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1007
Ya se ha definido el descriptor de acceso de la propiedad  
  
 Cuando declara una [propiedad](/dotnet/csharp/programming-guide/classes-and-structs/using-properties), también debe declarar los métodos de descriptor de acceso. Sin embargo, una propiedad no puede tener más de un método de descriptor de acceso `get` o más de un método de descriptor de acceso `set`.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS1007:  
  
```  
// CS1007.cs public class clx { public int MyProperty { get { return 0; } get   // CS1007, this is the second get method { return 0; } } public static void Main() {} }  
```