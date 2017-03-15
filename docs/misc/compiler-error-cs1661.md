---
title: "Error del compilador CS1661 | Microsoft Docs"
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
  - "CS1661"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1661"
ms.assetid: 162d5736-ca3c-4a09-a5d9-a19da3d5bf24
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1661
No se puede convertir el bloque de método anónimo al tipo de delegado 'delegate type' porque los tipos de parámetros del bloque especificado no coinciden con los tipos de parámetro de delegado  
  
 Este error se produce si, en una definición de método anónimo, los tipos de parámetro del método anónimo no coinciden los tipos de parámetro de delegado. Compruebe el número de parámetros, los tipos de parámetro y todos los parámetros ref o out, y confirme que la coincidencia es exacta.  
  
 El ejemplo siguiente genera la advertencia CS1661:  
  
```  
// CS1661.cs delegate void MyDelegate(int i); class C { public static void Main() { MyDelegate d = delegate(string s) { };  // CS1661 } }  
```