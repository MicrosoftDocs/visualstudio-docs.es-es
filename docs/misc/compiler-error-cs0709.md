---
title: "Error del compilador CS0709 | Microsoft Docs"
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
  - "CS0709"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0709"
ms.assetid: 91040f55-a060-4cc3-b830-f6b771af28d7
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0709
'clase derivada': no se puede derivar de la clase estática 'clase base'  
  
 No se puede crear una instancia de una clase estática ni se puede derivar. Es decir, una clase estática no puede ser una clase base de cualquier otra clase.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS0709.  
  
```  
// CS0709.cs // compile with: /target:library public static class Base {} public class Derived : Base {}   // CS0709  
```