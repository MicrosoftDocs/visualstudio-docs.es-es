---
title: "Advertencia del compilador (nivel 1) CS0672 | Microsoft Docs"
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
  - "CS0672"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0672"
ms.assetid: 140a8708-97d0-444b-980b-62e74328cafb
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 1) CS0672
El miembro 'member1' reemplaza al miembro obsoleto 'member2'. Agregue el atributo Obsolete a 'member1'.  
  
 El compilador encontró un `override` a un método marcado como `obsolete`. Sin embargo, el método de reemplazo no estaba marcado como obsoleto. El método de reemplazo seguirá generando [CS0612](../misc/compiler-warning-level-1-cs0612.md), si se le llama.  
  
 Revise sus declaraciones de método e indique explícitamente si debe marcarse un método \(y todos sus reemplazos\) `obsolete`.  
  
 El ejemplo siguiente genera la advertencia CS0672:  
  
```  
// CS0672.cs // compile with: /W:1 class MyClass { [System.Obsolete] public virtual void ObsoleteMethod() { } } class MyClass2 : MyClass { public override void ObsoleteMethod()   // CS0672 { } } class MainClass { static public void Main() { } }  
```