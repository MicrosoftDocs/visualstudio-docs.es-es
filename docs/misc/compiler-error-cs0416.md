---
title: "Error del compilador CS0416 | Microsoft Docs"
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
  - "CS0416"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0416"
ms.assetid: 61bfe40d-5e87-47e5-933f-3491e28ace42
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0416
'parámetro de tipo': un argumento de atributo no puede usar parámetros de tipo  
  
 Se usó un parámetro de tipo como un argumento de atributo, pero esto no se permite. Use un tipo no genérico.  
  
 El ejemplo siguiente genera la advertencia CS0416:  
  
```  
// CS0416.cs public class MyAttribute : System.Attribute { public MyAttribute(System.Type t) { } } class G<T> { [MyAttribute(typeof(G<T>))]  // CS0416 public void F() { } }  
```