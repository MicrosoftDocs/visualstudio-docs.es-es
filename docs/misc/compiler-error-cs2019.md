---
title: "Error del compilador CS2019 | Microsoft Docs"
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
  - "CS2019"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2019"
ms.assetid: eafd2531-8b3a-499c-9e12-a605a011396f
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS2019
Tipo de destino no válido para \/target: se debe especificar 'exe', 'winexe', 'library' o 'module'  
  
 Se usó la opción del compilador [\/target](/dotnet/csharp/language-reference/compiler-options/target-compiler-option), pero se pasó un parámetro no válido. Para resolver este error, vuelva a compilar el programa usando el formato de la opción **\/target** adecuado para el archivo de salida.  
  
 El ejemplo siguiente genera la advertencia CS2017:  
  
```  
// CS2019.cs // compile with: /target:libra // CS2019 expected class MyClass { }  
```