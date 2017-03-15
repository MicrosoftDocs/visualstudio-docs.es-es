---
title: "Error del compilador CS0409 | Microsoft Docs"
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
  - "CS0409"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0409"
ms.assetid: 23d86c13-7978-41b7-a087-ffcea52476fa
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0409
Ya se ha especificado una cláusula de restricción para el parámetro de tipo 'parámetro de tipo'. Todas las restricciones de un parámetro de tipo deben especificarse en una sola cláusula where.  
  
 Se encontraron varias cláusulas de restricción \(cláusulas where\) para un único parámetro de tipo. Quite la cláusula where extraña o corrija las cláusulas where para que haya un parámetro de tipo único en cada cláusula.  
  
```  
// CS0409.cs interface I { } class C<T1, T2> where T1 : I where T1 : I  // CS0409 – T1 used twice { }  
```