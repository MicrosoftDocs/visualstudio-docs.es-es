---
title: "Error del compilador CS0418 | Microsoft Docs"
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
  - "CS0418"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0418"
ms.assetid: b78fafde-428b-4fa2-a933-c4614760bb71
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0418
'class name': una clase abstracta no puede ser sellada ni estática  
  
 Una clase abstracta no puede usarse para crear objetos a menos que sea derivada, por lo que no tiene sentido que sea sellada. Una clase abstracta tampoco puede ser estática con sentido; las clases abstractas están diseñadas para admitir una jerarquía de objetos que usará la clase abstracta como base.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS0418:  
  
```  
// CS0418.cs public abstract sealed class C  // CS0418 { } sealed static class S  // CS0418 { } public class MyClass { public static void Main() { } }  
```