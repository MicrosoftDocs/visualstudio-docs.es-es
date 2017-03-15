---
title: "Advertencia del compilador (nivel 3) CS0105 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0105"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0105"
ms.assetid: 96d1d5d7-79e9-424f-bbde-f87e88b70003
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 3) CS0105
La directiva using para 'espacioDeNombres' aparece previamente en este espacio de nombres  
  
 Un [espacio de nombres](/dotnet/csharp/language-reference/keywords/namespace), que solo debe declararse una vez, se declaró más de una vez. Quite todas las declaraciones de espacio de nombre duplicadas.  
  
 El ejemplo siguiente genera la advertencia CS0105:  
  
```  
// CS0105.cs // compile with: /W:3 using System; using System;   // CS0105 public class a { public static void Main() { } }  
```