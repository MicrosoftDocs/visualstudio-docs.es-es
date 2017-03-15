---
title: "Error del compilador CS0451 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0451"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0451"
ms.assetid: e73544f8-856b-4a92-90e0-dd6cb9d688b1
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0451
La restricción 'new\(\)' no se puede utilizar con la restricción 'struct'  
  
 Al especificar restricciones en el tipo de un genérico, la restricción `new()` solo puede usarse con restricciones de tipo de clase, restricciones de tipo de interfaz, restricciones de tipo de referencia y restricciones de parámetro de tipo, pero no con restricciones de tipo de valor.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS0451.  
  
```  
// CS0451.cs using System; public class C4 { public void F4<T>() where T : struct, new() {}   // CS0451 } // OK public class C5 { public void F5<T>() where T : struct {} } public class C6 { public void F6<T>() where T : new() {} }  
  
```