---
title: "Error del compilador CS1650 | Microsoft Docs"
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
  - "CS1650"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1650"
ms.assetid: 251a3a67-6e56-4795-874a-d54610c70595
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1650
Los campos del campo de solo lectura estático 'identificador' no se pueden asignar \(excepto en un constructor estático o un inicializador de variables\).  
  
 Este error se produce cuando se intenta modificar un miembro de un campo que es estático y de solo lectura que no está permitida su modificación. Para resolver este error, limite las asignaciones a campos de solo lectura para el constructor o inicializador de variable o quite la palabra clave `readonly` de la declaración del campo.  
  
```  
// CS1650.cs public struct Inner { public int i; } class Outer { public static readonly Inner inner = new Inner(); } class D { static void Main() { Outer.inner.i = 1;  // CS1650 } }  
```