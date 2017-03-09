---
title: "Error del compilador CS0506 | Microsoft Docs"
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
  - "CS0506"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0506"
ms.assetid: 1286957c-2505-4b5f-ade0-154ad5f09dc1
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0506
'function1': no se puede invalidar el miembro heredado 'function2' porque no está marcado como "virtual", "abstract" ni "override"  
  
 Se reemplazó un método que no estaba marcado explícitamente como **virtual**, **abstract** ni `override`.  
  
 El ejemplo siguiente genera la advertencia CS0506:  
  
```  
// CS0506.cs namespace MyNameSpace { abstract public class ClassX { public int i = 0; public int f() { return 0; } // Try the following definition for f() instead: // abstract public int f(); } public class ClassY : ClassX { public override int f()   // CS0506 { return 0; } public static int Main() { return 0; } } }  
```