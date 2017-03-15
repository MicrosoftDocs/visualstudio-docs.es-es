---
title: "Error del compilador CS0425 | Microsoft Docs"
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
  - "CS0425"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0425"
ms.assetid: cec0391c-a641-43bc-8557-92b23f6ca685
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0425
Las restricciones del parámetro de tipo 'type parameter' del método 'method' deben coincidir con las restricciones del parámetro de tipo 'type parameter' del método de interfaz 'method'. Considere la posibilidad de usar una implementación de interfaz explícita en su lugar.  
  
 Este error se produce si un método genérico virtual se reemplaza en una clase derivada y las restricciones en el método de la clase derivada no coinciden con las restricciones en el método de la clase base. Para evitar este error, asegúrese de que la cláusula `where` es idéntica en ambas declaraciones o implemente la interfaz explícitamente.  
  
## Ejemplo  
 El ejemplo siguiente genera el error CS0425:  
  
```  
// CS0425.cs class C1 { } class C2 { } interface IBase { void F<ItemType>(ItemType item) where ItemType : C1; } class Derived : IBase { public void F<ItemType>(ItemType item) where ItemType : C2  // CS0425 { } } class CMain { public static void Main() { } }  
```  
  
## Ejemplo  
 Las restricciones no tienen que ser una coincidencia literal, siempre que el conjunto de restricciones tenga el mismo significado. Por ejemplo, el código siguiente es correcto:  
  
```  
// CS0425b.cs interface J<Z> { } interface I<S> { void F<T>(S s, T t) where T: J<S>, J<int>; } class C : I<int> { public void F<X>(int s, X x) where X : J<int> { } public static void Main() { } }  
```