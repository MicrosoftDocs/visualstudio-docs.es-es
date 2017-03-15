---
title: "Error del compilador CS0139 | Microsoft Docs"
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
  - "CS0139"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0139"
ms.assetid: 235ba3d4-566c-4ef6-801a-a338f4f2a12d
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0139
No hay ningún bucle envolvente desde el que interrumpir o continuar  
  
 Se ha encontrado una instrucción break o continue fuera de un bucle.  
  
 Para obtener más información, vea [Instrucciones de salto](/dotnet/csharp/language-reference/keywords/jump-statements).  
  
 El ejemplo siguiente genera la advertencia CS0139 dos veces:  
  
```  
// CS0139.cs namespace x { public class a { public static void Main() { continue;  // CS0139 break;     // CS0139 } } }  
```