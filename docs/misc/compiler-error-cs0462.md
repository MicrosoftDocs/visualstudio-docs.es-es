---
title: "Error del compilador CS0462 | Microsoft Docs"
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
  - "CS0462"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0462"
ms.assetid: 0732b12d-0f7a-47d5-bc54-8b6147d7249f
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0462
Los miembros heredados 'member1' y 'member2' tienen la misma firma en el tipo 'type', por lo que no se pueden reemplazar  
  
 Este error se produce con la introducción de genéricos. Normalmente, no se pueden tener dos versiones de un método en una clase con la misma firma. Pero con los genéricos, es posible especificar un método genérico que podría duplicar a otro si se crea una instancia con un tipo determinado.  
  
## Ejemplo  
 Cuando se crea una instancia de `C<int>`, se crean dos versiones del método `F` con la misma firma, por lo que el reemplazo de la clase `D` no puede decidir a cuál de ellas se debe aplicar el reemplazo.  
  
 El ejemplo siguiente genera la advertencia CS0462:  
  
```  
// CS0462.cs // compile with: /target:library class C<T> { public virtual void F(T t) {} public virtual void F(int t) {} } class D : C<int> { public override void F(int t) {}   // CS0462 }  
```