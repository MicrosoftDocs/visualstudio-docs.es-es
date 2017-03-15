---
title: "Error del compilador CS1024 | Microsoft Docs"
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
  - "CS1024"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1024"
ms.assetid: 41f587cb-1958-4eb6-9f8d-c03500e55e21
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1024
Se esperaba una directiva de preprocesador  
  
 Una línea comenzaba con el símbolo de libra \(\#\), pero la cadena siguiente no era una [directiva de preprocesador](/dotnet/csharp/language-reference/preprocessor-directives/index) válida.  
  
 El ejemplo siguiente genera la advertencia CS1024:  
  
```  
// CS1024.cs #import System   // CS1024  
```