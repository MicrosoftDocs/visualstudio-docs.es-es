---
title: "Advertencia del compilador (nivel 2) CS0114 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0114"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0114"
ms.assetid: 9647772b-d581-4620-981e-f9c607d4a1af
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 2) CS0114
'función1' oculta el miembro heredado 'función2'. Para hacer que el método actual reemplace esa implementación, agregue la palabra clave override. De lo contrario, agregue la palabra clave new.  
  
 Hay una declaración de una clase que tiene conflicto con una declaración de una clase base, de modo que se ocultará el miembro de la clase base.  
  
 Para obtener más información, vea [base](/dotnet/csharp/language-reference/keywords/base).  
  
 El ejemplo siguiente genera la advertencia CS0114:  
  
```  
// CS0114.cs // compile with: /W:2 /warnaserror abstract public class clx { public abstract void f(); } public class cly : clx { public void f() // CS0114, hides base class member // try the following line instead // override public void f() { } public static void Main() { } }  
```