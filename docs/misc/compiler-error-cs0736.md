---
title: "Error del compilador CS0736 | Microsoft Docs"
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
  - "CS0736"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0736"
ms.assetid: 06b14feb-81d5-495f-ab2d-6dc3f5e7216f
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0736
'type name' no implementa el miembro de interfaz 'member name'. 'method name' no puede implementar un miembro de interfaz porque no es estático.  
  
 Este error se genera cuando un método estático se declara de forma implícita o explícita como una implementación de un miembro de interfaz.  
  
### Para corregir este error  
  
-   Quite el modificador [static](/dotnet/csharp/language-reference/keywords/static) de la declaración del método.  
  
-   Cambie el nombre del método de la interfaz.  
  
-   Redefina el tipo de contenedor para que no se herede de la interfaz.  
  
## Ejemplo  
 El código siguiente genera CS0736 porque `Program.testMethod` está declarado como estático:  
  
```  
// cs0736.cs namespace CS0736 { interface ITest { int testMethod(int x); } class Program : ITest // CS0736 { public static int testMethod(int x) { return 0; } // Try the following line instead. // public int testMethod(int x) { return 0; } public static void Main() { } } }  
```  
  
## Vea también  
 [Interfaces](/dotnet/csharp/programming-guide/interfaces/index)