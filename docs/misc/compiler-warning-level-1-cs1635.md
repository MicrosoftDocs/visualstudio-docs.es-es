---
title: "Advertencia del compilador (nivel 1) CS1635 | Microsoft Docs"
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
  - "CS1635"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1635"
ms.assetid: e1795880-f7ea-4dca-b15b-4ba549d7ed78
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 1) CS1635
No se puede restaurar la advertencia 'warning code' porque estaba deshabilitada globalmente.  
  
 Esta advertencia se produce si usa la opción de línea de comandos **\/nowarn** o la configuración de proyecto para deshabilitar una advertencia en toda la unidad de compilación, pero usa `#pragma warning restore` para intentar restaurar dicha advertencia. Para resolver este error, quite la opción de línea de comandos \/nowarn o la configuración de proyecto, o quite el `#pragma warning restore` de cualquier advertencia que esté deshabilitando a través de la línea de comandos o la configuración del proyecto. Para más información, vea el tema [\#pragma \(advertencia\)](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning).  
  
 El ejemplo siguiente genera la advertencia CS1635:  
  
```  
// CS1635.cs // compile with: /w:1 /nowarn:162 enum MyEnum {one=1,two=2,three=3}; class MyClass { public static void Main() { #pragma warning disable 162 if (MyEnum.three == MyEnum.two) System.Console.WriteLine("Duplicate"); #pragma warning restore 162 } }  
```