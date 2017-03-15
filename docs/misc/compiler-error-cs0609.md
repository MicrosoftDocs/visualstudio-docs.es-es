---
title: "Error del compilador CS0609 | Microsoft Docs"
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
  - "CS0609"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0609"
ms.assetid: f3ff07a6-1190-4a1c-86a5-f607e1a32b78
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0609
No se puede establecer el atributo IndexerName en un indizador marcado como override  
  
 El atributo de nombre \(**IndexerNameAttribute**\) no se puede aplicar a una propiedad indexada que sea un reemplazo. Para más información, vea [Indizadores](/dotnet/csharp/programming-guide/indexers/index).  
  
 El ejemplo siguiente genera la advertencia CS0609:  
  
```  
// CS0609.cs using System; using System.Runtime.CompilerServices; public class idx { public virtual int this[int iPropIndex] { get { return 0; } set { } } } public class MonthDays : idx { [IndexerName("MonthInfoIndexer")]   // CS0609, delete to resolve this CS0609 public override int this[int iPropIndex] { get { return 0; } set { } } } public class test { public static void Main( string[] args ) { } }  
```