---
title: "Advertencia de conformidad con CLS CLS01506 | Microsoft Docs"
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
  - "CLS01506"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01506"
ms.assetid: 030f1b81-1159-4057-9fee-8721a419a5d6
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Advertencia de conformidad con CLS CLS01506
La restricción varargs no forma parte de CLS  
  
 La restricción varargs no forma parte de Common Language Subset \(CLS\).  La única convención de llamada que admite CLS es la convención de llamada administrada estándar.  
  
 Para más información sobre la comprobación de conformidad con CLS, vea [Ensamblados conformes con CLS](http://msdn.microsoft.com/es-es/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 La siguiente declaración de función \(mediante el lenguaje ensamblador MSIL\) muestra lo que podría provocar la advertencia CLS01506:  
  
```  
.method public instance vararg void  Method1() cil managed  
```  
  
 Si se quita la palabra clave **vararg**, se puede resolver esta advertencia:  
  
```  
.method public instance void  Method1() cil managed  
```