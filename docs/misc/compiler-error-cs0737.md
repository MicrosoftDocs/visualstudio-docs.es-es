---
title: "Error del compilador CS0737 | Microsoft Docs"
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
  - "CS0737"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0737"
ms.assetid: d2247770-5546-46f2-a01d-8e2ebfcbb859
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0737
'type name' no implementa el miembro de interfaz 'member name'. 'method name' no puede implementar un miembro de interfaz porque no es público.  
  
 Un método que implementa a un miembro de interfaz debe tener accesibilidad pública. Todos los miembros de interfaz son `public`.  
  
### Para corregir este error  
  
1.  Agregue al método el modificador de acceso [public](/dotnet/csharp/language-reference/keywords/public).  
  
## Ejemplo  
 El código siguiente genera CS0737:  
  
```  
// cs0737.cs interface ITest { // Default access of private with no modifier. int Return42(); // Try the following line instead. // public int Return42(); } struct Struct1 : ITest // CS0737 { int Return42() { return (42); } } public class Test { public static int Main(string[] args) { Struct1 s1 = new Struct1(); return (1); } }  
```  
  
## Vea también  
 [Interfaces](/dotnet/csharp/programming-guide/interfaces/index)