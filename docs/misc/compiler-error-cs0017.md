---
title: "Error del compilador CS0017 | Microsoft Docs"
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
  - "CS0017"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0017"
ms.assetid: 5e2a3eb3-6f6e-485d-8293-ceabea4d6905
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0017
El programa 'nombre de archivo de salida' tiene más de un punto de entrada definido. Compile con \/main para especificar el tipo que contiene el punto de entrada.  
  
 Un programa puede tener un solo método [Main](/dotnet/csharp/programming-guide/main-and-command-args/main-and-command-line-arguments).  
  
 Para resolver este error, puede eliminar todos los métodos Main del código, salvo uno, o bien puede usar la opción del compilador [\/main](/dotnet/csharp/language-reference/compiler-options/main-compiler-option) para especificar qué método Main que se va a usar.  
  
 El ejemplo siguiente genera la advertencia CS0017:  
  
```  
// CS0017.cs // compile with: /target:exe public class clx { static public void Main() { } } public class cly { public static void Main()   // CS0017, delete one Main or use /main { } }  
```