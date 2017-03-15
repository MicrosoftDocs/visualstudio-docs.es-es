---
title: "Error del compilador CS1542 | Microsoft Docs"
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
  - "CS1542"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1542"
ms.assetid: d7f60aa2-6645-472c-ac12-fa57a09fbd87
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1542
No se puede agregar 'dll' a este ensamblado porque ya es un ensamblado; utilice la opción '\/R' en su lugar  
  
 El archivo al que se hizo referencia con la opción del compilador [\/addmodule](/dotnet/csharp/language-reference/compiler-options/addmodule-compiler-option) no se generó con [\/target:module](../Topic/-target:module%20\(C%23%20Compiler%20Options\).md); use [\/reference](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option) para hacer referencia al archivo en esta compilación.