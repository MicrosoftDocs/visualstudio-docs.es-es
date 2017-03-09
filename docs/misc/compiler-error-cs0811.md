---
title: "Error del compilador CS0811 | Microsoft Docs"
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
  - "CS0811"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0811"
ms.assetid: 99f81ad3-684f-47aa-adb8-360e24901454
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0811
El nombre completo de 'nombre' es demasiado largo para la información de depuración. Compile sin la opción '\/debug'.  
  
 Existen restricciones de tamaño para los nombres de variable y tipo en la información de depuración.  
  
### Para corregir este error  
  
1.  Si no es posible modificar el nombre, la única alternativa consiste en compilar sin la opción [\/debug](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option).  
  
## Ejemplo  
 El código siguiente genera el error CS0811:  
  
```  
// cs0811.cs //Compile with: /debug using System; using System.Collections.Generic; namespace TestNamespace { using Long = List<List<List<List<List<List<List<List<List<List<List<List<List <List<List<List<List<List<List<List<List<List<List<List<List<List<List<List<int>>>>>>>>>>>>>>>>>>>>>>>>>>>>; // CS0811 class Test { static int Main() { return 1; } } }  
```