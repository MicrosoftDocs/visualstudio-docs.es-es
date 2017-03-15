---
title: "Error del compilador CS0738 | Microsoft Docs"
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
  - "CS0738"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0738"
ms.assetid: 01ce94ee-2435-4326-befc-2b020c441a4f
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0738
'nombre de tipo' no implementa el miembro de interfaz 'nombre de miembro'. 'nombre de método' no implementa 'miembro de interfaz' porque no tiene el tipo de valor devuelto coincidente de 'nombre de tipo'.  
  
 El valor devuelto de un método de implementación en una clase debe coincidir con el valor devuelto del miembro de interfaz que implementa.  
  
### Para corregir este error  
  
1.  Cambie el tipo de valor devuelto del método para que coincida con el del miembro de interfaz.  
  
## Ejemplo  
 El código siguiente genera el error CS0738 porque el método de clase devuelve `void` y el miembro de interfaz del mismo nombre devuelve `int`:  
  
```  
using System; interface ITest { int TestMethod(); } public class Test: ITest { public void TestMethod() { } // CS0738 // Try the following line instead. // public int TestMethod(); }  
```  
  
## Vea también  
 [Interfaces](/dotnet/csharp/programming-guide/interfaces/index)