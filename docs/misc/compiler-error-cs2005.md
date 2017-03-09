---
title: "Error del compilador CS2005 | Microsoft Docs"
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
  - "CS2005"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2005"
ms.assetid: 03535d2a-ae30-4272-ab45-e277df5ee8e1
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS2005
Falta la especificación de archivo de la opción 'option'  
  
 Una [opción del compilador](/dotnet/csharp/language-reference/compiler-options/index) solo se especificó parcialmente.  
  
 Por ejemplo, si usa [\/recurse](/dotnet/csharp/language-reference/compiler-options/recurse-compiler-option), debe especificar el archivo que se buscará: **\/recurse:***nombre de archivo***.cs**.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS2005.  
  
```  
// CS2005.cs // compile with: /recurse: // CS2005 expected class x { public static void Main() {} }  
```