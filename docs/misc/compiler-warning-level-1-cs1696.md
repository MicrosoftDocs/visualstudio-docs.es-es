---
title: "Advertencia del compilador (nivel 1) CS1696 | Microsoft Docs"
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
  - "CS1696"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1696"
ms.assetid: 69a45988-1aba-4a01-a84e-7ca59f8dde28
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 1) CS1696
Se esperaba un comentario de una línea o un fin de línea  
  
 El compilador requiere que una directiva de preprocesador incluya a continuación un terminador de final de línea o una sola línea de comentario. El compilador ha terminado de procesar una directiva de preprocesador válida y ha encontrado algo que infringe esta restricción de sintaxis.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS1696.  
  
```  
// CS1696.cs class Test { public static void Main() { #pragma warning disable 1030;219   // CS1696 #pragma warning disable 1030   // OK } }  
```