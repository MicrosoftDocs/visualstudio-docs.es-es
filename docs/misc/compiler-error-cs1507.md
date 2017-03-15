---
title: "Error del compilador CS1507 | Microsoft Docs"
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
  - "CS1507"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1507"
ms.assetid: e1be3aba-81dc-4f65-87a4-d3f90b82dc7d
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1507
No se puede vincular archivos de recursos 'file' al compilar un módulo  
  
 [\/linkresource](/dotnet/csharp/language-reference/compiler-options/linkresource-compiler-option) se usó en la misma compilación con [\/target:module](../Topic/-target:module%20\(C%23%20Compiler%20Options\).md), lo que no está permitido. Por ejemplo, las siguientes opciones generaría CS1507:  
  
```  
csc /linkresource:rf.resource /target:module in.cs  
```  
  
 La incrustación de recursos \([\/resource](/dotnet/csharp/language-reference/compiler-options/resource-compiler-option)\), sin embargo, sí se permite.