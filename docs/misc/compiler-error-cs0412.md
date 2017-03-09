---
title: "Error del compilador CS0412 | Microsoft Docs"
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
  - "CS0412"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0412"
ms.assetid: eeb2afbc-9416-4bcf-b116-d6adc5cfd4ca
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0412
'generic': un parámetro o una variable local no puede tener el mismo nombre que un parámetro de tipo de método  
  
 Existe un conflicto de nombres entre el parámetro de tipo de un método genérico y una variable local del método o uno de los parámetros del método. Para evitar este error, cambie el nombre de los parámetros o las variables locales en conflicto.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS0412:  
  
```  
// CS0412.cs using System; class C { // Parameter name is the same as method type parameter name public void G<T>(int T)  // CS0412 { } public void F<T>() { // Method local variable name is the same as method type // parameter name double T = 0.0;  // CS0412 Console.WriteLine(T); } public static void Main() { } }  
```