---
title: "Error del compilador CS1016 | Microsoft Docs"
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
  - "CS1016"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1016"
ms.assetid: 576e6e12-981c-43b6-9e4a-29fa4e9f76e8
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1016
Se esperaba un argumento de atributo con nombre  
  
 Los argumentos de atributo sin nombre deben aparecer antes que los argumentos con nombre.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS1016:  
  
```  
// CS1016.cs using System; [AttributeUsage(AttributeTargets.Class)] public class HelpAttribute : Attribute { public HelpAttribute(string url)   // url is a positional parameter { m_url = url; } public string Topic = null;      // Topic is a named parameter private string m_url = null; } [HelpAttribute(Topic="Samples", "http://intranet/inhouse")]   // CS1016 // try the following line instead //[HelpAttribute("http://intranet/inhouse", Topic="Samples")] public class MainClass { public static void Main () { } }  
```