---
title: "Advertencia de conformidad con CLS CLS01501 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CLS01501"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01501"
ms.assetid: 74361331-3773-48d5-8508-0113f5464a75
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Advertencia de conformidad con CLS CLS01501
**La restricción varargs no forma parte de CLS**  
  
 La restricción varargs no forma parte de Common Language Subset \(CLS\).  La única convención de llamada que admite CLS es la convención de llamada administrada estándar.  
  
 Para más información sobre la comprobación de conformidad con CLS, vea [CLS Compliant Assemblies](http://msdn.microsoft.com/es-es/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 La siguiente declaración de función \(mediante el lenguaje ensamblador MSIL\) muestra lo que podría provocar la advertencia CLS01501:  
  
```  
.method public specialname rtspecialname instance vararg void  .ctor() cil managed  
```  
  
 Puede resolver CLS01501 usando una matriz de parámetros.  Vea [Listas de argumentos de variables \(...\) \(C\+\+\/CLI\)](/visual-cpp/windows/variable-argument-lists-dot-dot-dot-cpp-cli) para más información.