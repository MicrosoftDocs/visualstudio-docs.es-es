---
title: "Error del compilador CS0681 | Microsoft Docs"
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
  - "CS0681"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0681"
ms.assetid: aa51ad94-df0a-481d-aaea-5b4291ebc41c
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0681
El modificador 'abstract' no es válido en los campos. Pruebe a usar una propiedad en su lugar.  
  
 No se puede hacer que un campo sea abstracto. Sin embargo, puede tener una propiedad abstracta que tenga acceso al campo.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS0681:  
  
```  
// CS0681.cs // compile with: /target:library abstract class C { abstract int num;  // CS0681 }  
  
```  
  
## Ejemplo  
 Pruebe en su lugar el código siguiente:  
  
```  
// CS0681b.cs // compile with: /target:library abstract class C { public abstract int num { get; set; } }  
```