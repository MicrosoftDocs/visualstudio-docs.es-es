---
title: "Advertencia del compilador (nivel 2) CS1927 | Microsoft Docs"
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
  - "CS1927"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1927"
ms.assetid: 32b4e58f-668c-4596-9529-7f3a293ff4ac
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 2) CS1927
Se omitirá \/win32manifest para el módulo porque solo se aplica a ensamblados.  
  
 Un manifiesto win32 solo se aplica en el nivel de ensamblado. El módulo se compilará, pero no tendrá un manifiesto.  
  
### Para corregir este error  
  
1.  Quite el **\/win32manifest option**.  
  
2.  Compile el código como un ensamblado.  
  
## Ejemplo  
 El ejemplo siguiente genera el error CS1927 cuando se compila con las dos opciones del compilador **\/target:module** y **\/win32manifest**.  
  
```  
// cs1927.cs // Compile with: /target:module /win32manifest using System; class ManifestWithModule { static int Main() { return 1; } }  
```  
  
## Vea también  
 [\/win32manifest \(Import a Custom Win32 Manifest File\)](/dotnet/csharp/language-reference/compiler-options/win32manifest-compiler-option)   
 [\/target:module \(Create Module to Add to Assembly\)](../Topic/-target:module%20\(C%23%20Compiler%20Options\).md)