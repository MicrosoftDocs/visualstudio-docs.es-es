---
title: "Error del compilador CS0713 | Microsoft Docs"
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
  - "CS0713"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0713"
ms.assetid: 27a46765-d982-43ba-909f-9278e26b80d2
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0713
La clase estática 'tipo estático' no se puede derivar del tipo 'tipo'. Las clases estáticas se deben derivar del objeto.  
  
 Si se permitiera, la clase estática heredaría métodos y miembros no estáticos de la clase base, por lo que no sería estática. Por lo tanto, no se permite.  
  
 El ejemplo siguiente genera la advertencia CS0713:  
  
```  
// CS0713.cs public class Base { } public static class Derived : Base  // CS0713 { } public class CMain { public static void Main() { } }  
```