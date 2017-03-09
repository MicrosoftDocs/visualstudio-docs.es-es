---
title: "Advertencia del compilador (nivel 1) CS2002 | Microsoft Docs"
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
  - "CS2002"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2002"
ms.assetid: 4acd054e-d3fe-4be6-a660-53a0a5e8c6a4
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 1) CS2002
Se especificó el archivo de código fuente 'file' varias veces  
  
 El nombre de un archivo de código fuente se pasó al compilador más de una vez. Solo se puede especificar un archivo una vez en el compilador para compilar un archivo de salida.  
  
 No se puede suprimir esta advertencia mediante la opción [\/nowarn](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option).  
  
 El ejemplo siguiente genera la advertencia CS2002:  
  
```  
// CS2002.cs // compile with: CS2002.cs public class A { public static void Main(){} }  
```  
  
 Para generar el error, compile el ejemplo con la línea de comandos:  
  
```  
csc CS2002.cs CS2002.cs  
```