---
title: "Error del compilador CS1638 | Microsoft Docs"
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
  - "CS1638"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1638"
ms.assetid: 5279c060-5be3-4c29-80cc-21326d4cffdb
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1638
'identificador' es un identificador reservado y no se puede usar cuando se usa el modo de versión de lenguaje ISO.  
  
 Cuando el conmutador de compilador **\/langversion** especifica la opción de compatibilidad de lenguaje ISO, los identificadores que contengan caracteres dobles de subrayado en cualquier lugar generarán este error. Para evitar este error, elimine los identificadores con caracteres dobles de subrayado o no use la opción de versión de lenguaje ISO\-1.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS1638:  
  
```  
// CS1638.cs // compile with: /langversion:ISO-1 class bad__identifer // CS1638 (double underscores are not ISO compliant) { } // Try this instead: //class GoodIdentifier //{ //} class CMain { public static void Main() { } }  
```  
  
## Vea también  
 [\/langversion \(Conformant Syntax\)](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option)