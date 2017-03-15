---
title: "Error del compilador CS0734 | Microsoft Docs"
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
  - "CS0734"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0734"
ms.assetid: 9e1b0e49-bfc3-400c-9fd1-37e3c827e656
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0734
La opción \/moduleassemblyname únicamente se puede especificar cuando cree un tipo de destino de 'module'  
  
 La opción del compilador **\/moduleassemblyname** solo se debe utilizar al compilar un archivo .netmodule. Vea [\/moduleassemblyname \(Specify Friend Assembly for Module\)](/dotnet/csharp/language-reference/compiler-options/moduleassemblyname-compiler-option) para obtener más información.  
  
 Para más información sobre cómo compilar un archivo .netmodule, vea [\/target:module \(Create Module to Add to Assembly\)](../Topic/-target:module%20\(C%23%20Compiler%20Options\).md).  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS0734. Para solucionarlo, agregue **\/target:module** a la compilación.  
  
```  
// CS0734.cs // compile with: /moduleassemblyname:A // CS0734 expected public class Test {}  
```