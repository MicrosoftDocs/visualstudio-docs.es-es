---
title: "Error del compilador CS0698 | Microsoft Docs"
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
  - "CS0698"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0698"
ms.assetid: 68211652-fdfa-4d37-9451-f0b4238f9fe6
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0698
Un tipo genérico no puede derivar de 'class' porque se trata de una clase de atributos  
  
 Una clase que derive de una clase de atributo es un atributo. No se permite que los atributos sean tipos genéricos.  
  
 El ejemplo siguiente genera la advertencia CS0698:  
  
```  
// CS0698.cs class C<T> : System.Attribute  // CS0698 { }  
```