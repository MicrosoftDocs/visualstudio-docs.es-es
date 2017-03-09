---
title: "Advertencia del compilador (nivel 2) CS0464 | Microsoft Docs"
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
  - "CS0464"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0464"
ms.assetid: 3dff97d4-e1f6-4a71-91e2-68cffc38d49a
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 2) CS0464
Comparar con tipos de estructura o nulos siempre produce 'false'  
  
 Esta advertencia se genera cuando se efectúa una comparación entre una variable que admite null y null, y la comparación no es `==` ni `!=`. Para resolver este error, compruebe si realmente desea comprobar un valor para `null`. Una comparación como `i == null` puede ser true o false. Una comparación como `i > null` siempre es false.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS0464.  
  
```  
// CS0464.cs class MyClass { public static void Main() { int? i = 0; if (i < null) ;   // CS0464 i++; } }  
```