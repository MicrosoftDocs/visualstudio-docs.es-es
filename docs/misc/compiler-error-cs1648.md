---
title: "Error del compilador CS1648 | Microsoft Docs"
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
  - "CS1648"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1648"
ms.assetid: 5cf1bc84-cd18-4df2-942f-1cc17eabacd6
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1648
Los miembros del campo de solo lectura 'identificador' no se pueden modificar \(excepto en un constructor o en un inicializador de variable\)  
  
 Este error se produce cuando se intenta modificar un miembro de un campo que es de solo lectura donde no se permite su modificación. Para resolver este error, limite las asignaciones en campos de solo lectura al constructor o al inicializador de variable, o bien quite la palabra clave readonly de la declaración del campo.  
  
 El ejemplo siguiente genera la advertencia CS1648:  
  
```  
// CS1648.cs public struct Inner { public int i; } class Outer { public readonly Inner inner = new Inner(); } class D { static void Main() { Outer outer = new Outer(); outer.inner.i = 1;  // CS1648 } }  
```