---
title: "Error del compilador CS0529 | Microsoft Docs"
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
  - "CS0529"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0529"
ms.assetid: 61de8086-f991-455c-b009-bb8cd05f34bd
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0529
La interfaz heredada 'interfaz1' genera un ciclo en la jerarquía de la interfaz 'interfaz2'  
  
 La lista de herencia de una [interfaz](/dotnet/csharp/language-reference/keywords/interface) incluye una referencia directa o indirecta a sí misma. La interfaz no puede heredar de sí misma.  
  
 El ejemplo siguiente genera la advertencia CS0529:  
  
```  
// CS0529.cs namespace x { public interface a { } public interface b : a, c { } public interface c : b   // CS0529, b inherits from c { } }  
```