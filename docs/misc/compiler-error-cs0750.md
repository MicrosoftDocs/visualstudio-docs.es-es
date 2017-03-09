---
title: "Error del compilador CS0750 | Microsoft Docs"
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
  - "CS0750"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0750"
ms.assetid: 84fb6841-7f47-405a-ae05-95567692f73d
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0750
Un método parcial no puede tener modificadores de acceso ni los modificadores virtual, abstract, override, new, sealed o extern.  
  
 Debido a su comportamiento especial, los métodos parciales están sujetos a restricciones en cuanto a los modificadores que pueden aceptar.  
  
### Para corregir este error  
  
1.  Quite el modificador no autorizado de la declaración del método.  
  
## Ejemplo  
 El siguiente ejemplo genera el error CS0750:  
  
```  
// cs0750.cs using System; public class Base { protected virtual void PartG() { } protected void PartH() { } protected virtual void PartI() { } } public partial class C:Base { // All these partial method declarations // will generate CS0750. public partial void PartA(); private partial void PartB(); protected partial void PartC(); internal partial void PartD(); virtual partial void PartE(); abstract partial void PartF(); override partial void PartG(); new partial void PartH(); sealed override partial void PartI(); extern partial void PartJ(); public static int Main() { return 1; } }  
```  
  
## Vea también  
 [Clases y métodos parciales](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)