---
title: "Error del compilador CS1678 | Microsoft Docs"
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
  - "CS1678"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1678"
ms.assetid: 2be8aa17-81e2-47b0-b239-e41e0c5c0d97
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1678
El parámetro 'número' se declaró como tipo 'tipo1', pero debería ser 'tipo2'  
  
 Este error se produce cuando el tipo de parámetro de un método anónimo no coincide con la declaración del delegado al que se va a convertir el método.  
  
 El ejemplo siguiente genera la advertencia CS1678:  
  
```  
// CS1678 delegate void D(int i); class Errors { static void Main() { D d = delegate(string s) { };   // CS1678 // To resolve, use the following line instead: // D d = delegate(int s) { }; } }  
```