---
title: "Error del compilador CS0724 | Microsoft Docs"
ms.custom: ""
ms.date: "10/01/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0724"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0724"
ms.assetid: bcdb2017-7a43-4242-b4e2-a1ae03d6d73f
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0724
No necesita ningún atributo CLSCompliant porque el ensamblado no tiene ningún atributo CLSCompliant  
  
 En el ejemplo siguiente se genera el error CS0724 debido a la instrucción `throw` dentro del bloque de cláusulas `finally`.  
  
## Ejemplo  
 El siguiente ejemplo genera el error CS0724.  
  
```  
// CS0724.cs using System; class X { static void Test() { try { throw new Exception(); } catch { try { } finally { throw; // CS0724 } } } static void Main() { } }  
```