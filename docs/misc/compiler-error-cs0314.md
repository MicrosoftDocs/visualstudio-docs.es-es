---
title: "Error del compilador CS0314 | Microsoft Docs"
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
  - "CS0314"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0314"
ms.assetid: 12f68f51-0568-4e80-b0fd-15899807477d
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0314
El tipo 'tipo1' no se puede usar como parámetro de tipo 'nombre' en el tipo o método genérico 'nombre'. No hay ninguna conversión boxing o conversión de parámetros de tipo de 'type1' a 'type2'.  
  
 Cuando un tipo genérico usa un parámetro de tipo que está restringido, la nueva clase también debe cumplir las mismas restricciones.  
  
### Para corregir este error  
  
1.  En el ejemplo siguiente, agregue `where T : ClassConstraint` a la clase `B`.  
  
## Ejemplo  
 El código siguiente genera CS0314:  
  
```  
// cs0314.cs // Compile with: /target:library public class ClassConstraint { } public class A<T> where T : ClassConstraint { } public class B<T> : A<T> //CS0314 { } // Try using this instead. public class C<T> : A<T> where T : ClassConstraint { }  
```  
  
## Vea también  
 [Restricciones de tipos de parámetros](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters)