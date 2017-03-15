---
title: "Error del compilador CS0262 | Microsoft Docs"
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
  - "CS0262"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0262"
ms.assetid: 44f8661f-c934-483f-84cd-00ca8257e50a
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0262
Las declaraciones parciales de 'tipo' tienen modificadores de accesibilidad conflictivos.  
  
 Este error se produce si un tipo parcial tiene modificadores incoherentes como public, private, protected, internal o abstract. Estos modificadores deben ser coherentes en todas las declaraciones parciales para ese tipo. Para obtener más información, consulta [Clases y métodos parciales](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods).  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS0262:  
  
```  
// CS0262.cs class A { public partial class C  // CS0262 { } private partial class C { } }  
```