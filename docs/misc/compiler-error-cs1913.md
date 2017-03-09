---
title: "Error del compilador CS1913 | Microsoft Docs"
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
  - "CS1913"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1913"
ms.assetid: 652494b3-9576-4a4c-a9ee-695f86c4a023
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1913
El miembro 'name' no se puede inicializar. No es un campo ni una propiedad.  
  
 Los inicializadores de objeto solo se pueden usar para inicializar campos o propiedades accesibles.  
  
### Para corregir este error  
  
1.  Inicialice al miembro de clase en un constructor normal u otro método de inicialización.  
  
## Ejemplo  
 El ejemplo siguiente genera el error CS1913:  
  
```  
// cs1912.cs class A { public delegate void D(); public event D myEvent; } public class Test { static void Main() { A a = new A() {myEvent = M}; // CS1913 } public void M(){} }  
```  
  
## Vea también  
 [Clases y structs](/dotnet/csharp/programming-guide/classes-and-structs/index)