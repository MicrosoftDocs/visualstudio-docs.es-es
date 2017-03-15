---
title: "Error del compilador CS2036 | Microsoft Docs"
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
  - "CS2036"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2036"
ms.assetid: 44b73be4-b792-4735-bdbd-bd757ab22683
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS2036
La opción \/pdb necesita que se use también la opción \/debug.  
  
 Solo se generan archivos de base de datos de programa para las compilaciones de depuración. Por lo tanto, la opción **\/pdb** no tiene sentido en una compilación comercial.  
  
### Para corregir este error  
  
-   Agregue la opción del compilador **\/debug**.  
  
-   Elimine la opción del compilador **\/pdb**.  
  
## Ejemplo  
 El ejemplo siguiente genera el error CS2036 cuando se compila con la opción **\/pdb** pero sin la opción \/debug:  
  
```  
// cs2036.cs // Compile with: /pdb // CS2036 class Test { public static int Main() { return 1; } }  
```  
  
## Vea también  
 [\/pdb \(Specify Debug Symbol File\)](/dotnet/csharp/language-reference/compiler-options/pdb-compiler-option)   
 [\/debug \(Emit Debugging Information\)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option)