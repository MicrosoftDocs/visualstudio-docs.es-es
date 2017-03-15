---
title: "Error del compilador CS1928 | Microsoft Docs"
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
  - "CS1928"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1928"
ms.assetid: bcc9dbef-ded5-4ddd-8c03-a9837cb6d165
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1928
'Type' no contiene una definición para 'method' y el mejor 'method' de sobrecarga del método de extensión tiene algunos argumentos no válidos.  
  
 Este error se produce cuando el compilador no puede encontrar un miembro de clase con el nombre del método llamado. Puede encontrar un método de extensión con ese nombre, pero no con una firma que coincida con los tipos pasados con la llamada de método.  
  
### Para corregir este error  
  
1.  Pase tipos que coincidan con un método de extensión o un método de clase existente.  
  
## Ejemplo  
 El código siguiente genera el error CS1928:  
  
```  
// cs1928.cs class Test { static void Main() { Test t = new Test(); t.M("hi"); // CS1928 } } static class Ext { public static void M(this Test t, int i) { } }  
```  
  
 Este error suele ir acompañado del error CS1503: Argumento 'n': no se puede convertir de 'typeA' a 'typeB'.  
  
## Vea también  
 [Métodos de extensión](/dotnet/csharp/programming-guide/classes-and-structs/extension-methods)