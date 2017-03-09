---
title: "Advertencia del compilador (nivel 2) CS0652 | Microsoft Docs"
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
  - "CS0652"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0652"
ms.assetid: 1ec1cee6-858a-4104-aa15-2668723c6331
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 2) CS0652
La comparación con la constante integral no es válida; la constante está fuera del intervalo del tipo 'type'  
  
 El compilador detectó una comparación entre una constante y una variable donde la constante está fuera del rango de la variable.  
  
 El ejemplo siguiente genera la advertencia CS0652:  
  
```  
// CS0652.cs // compile with: /W:2 public class Class1 { private static byte i = 0; public static void Main() { short j = 256; if (i == 256)   // CS0652, 256 is out of range for byte i = 0; } }  
```