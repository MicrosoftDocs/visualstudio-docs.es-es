---
title: "Error del compilador CS0265 | Microsoft Docs"
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
  - "CS0265"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0265"
ms.assetid: d43d19c2-8a66-4bb1-95a0-557b0a29bce1
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0265
Las declaraciones parciales de 'type' tienen restricciones incoherentes para el parámetro de tipo 'type parameter'  
  
 Este error se produce cuando se define una clase genérica como clase parcial para que sus definiciones parciales aparezcan en más de un lugar y las restricciones del tipo genérico son incoherentes o distintas en dos o más lugares. Si especifica las restricciones en más de un lugar, todas deben ser idénticas. La solución más sencilla es especificar las restricciones en un lugar y omitirlas en los demás lugares. Para obtener más información, vea [Clases y métodos parciales](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods) y [Restricciones de tipos de parámetros](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters).  
  
 El código siguiente genera el error CS0265.  
  
## Ejemplo  
 En este código, las definiciones de clase parcial se encuentran en un único archivo, pero también se pueden distribuir en varios archivos.  
  
```  
// CS0265.cs public class GenericsErrors { interface IFace1 { } interface IFace2 { } partial class PartialBadBounds<T> where T : IFace1 { } // CS0265 partial class PartialBadBounds<T> where T : IFace2 { } }  
```