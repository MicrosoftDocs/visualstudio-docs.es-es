---
title: "Error del compilador CS0722 | Microsoft Docs"
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
  - "CS0722"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0722"
ms.assetid: 85f6854c-581d-482b-b4b0-1e665d9e3e6f
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0722
'type': los tipos estáticos no se pueden usar como tipos de valores devueltos  
  
 Un tipo estático como un tipo de valor devuelto no es significativo, ya que no se pueden crear instancias de tipos estáticos.  
  
 El ejemplo siguiente genera la advertencia CS0722:  
  
```  
// CS0722.cs public static class SC { } public class CMain { public SC F()  // CS0722 { return null; } public static void Main() { } }  
```