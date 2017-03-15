---
title: "Advertencia del compilador (nivel 3) CS0660 | Microsoft Docs"
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
  - "CS0660"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0660"
ms.assetid: 2f77b45b-c5c6-46af-abe9-002e67887896
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 3) CS0660
'clase' define el operador \=\= o el operador \!\=, pero no invalida Object.Equals\(object o\)  
  
 El compilador detectó el operador de igualdad o desigualdad definido por el usuario, pero no detectó ninguna invalidación para la función **Equals**. Un operador de igualdad o desigualdad definido por el usuario implica que también se desea invalidar la función **Equals**. Para obtener más información, consulte [NO ESTÁ EN LA COMPILACIÓN: Directrices para invalidar Equals\(\) y el operador \=\= \(Guía de programación de C\#\)](http://msdn.microsoft.com/es-es/7e4c24c5-7693-4c45-88fb-ba5204fbcb20).  
  
 El ejemplo siguiente genera la advertencia CS0660:  
  
```  
// CS0660.cs // compile with: /W:3 /warnaserror class Test   // CS0660 { public static bool operator == (object o, Test t) { return true; } // uncomment the Equals function to resolve // public override bool Equals(object o) // { //    return true; // } public override int GetHashCode() { return 0; } public static void Main() { } }  
```