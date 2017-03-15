---
title: "Error del compilador CS5001 | Microsoft Docs"
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
  - "CS5001"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS5001"
ms.assetid: e1e26e75-84e0-47c7-be8a-3c4fd0d6f497
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS5001
El programa 'program' no contiene ningún método 'Main' estático adecuado para un punto de entrada  
  
 Este error se produce cuando ningún método [Main](/dotnet/csharp/programming-guide/main-and-command-args/main-and-command-line-arguments) estático con una firma correcta se encuentra en el código que genera un archivo ejecutable. Este error también se produce si la función del punto de entrada, `Main`, se define con el caso incorrecto, como minúsculas `main`.  
  
-   `Main` se debe declarar como estático y debe devolver [void](/dotnet/csharp/language-reference/keywords/void) o [int](/dotnet/csharp/language-reference/keywords/int), y o bien no debe ningún parámetro o debe tener un parámetro más del tipo `string[]`.  
  
## Ejemplo  
 El ejemplo siguiente genera el error CS5001:  
  
```  
// CS5001.cs // CS5001 expected public class a { // Uncomment the following line to resolve. // static void Main() {} }  
```  
  
## Vea también  
 [Main\(\) y argumentos de la línea de comandos](/dotnet/csharp/programming-guide/main-and-command-args/main-and-command-line-arguments)