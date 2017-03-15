---
title: "Advertencia de conformidad con CLS CLS01512 | Microsoft Docs"
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
  - "CLS01512"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01512"
ms.assetid: 15822eb3-43b1-4d58-a22d-9532e5820008
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Advertencia de conformidad con CLS CLS01512
La restricción varargs no forma parte de CLS  
  
 La restricción varargs no forma parte de Common Language Subset \(CLS\).  La única convención de llamada que se admite en CLS es la convención de llamada administrada estándar.  
  
 Para más información sobre la comprobación de conformidad con CLS, vea [CLS Compliant Assemblies](http://msdn.microsoft.com/es-es/3320b57e-ea55-4697-a17d-f509a36a3c93) \(Ensamblados conformes a CLS\).  
  
 La siguiente declaración de función \(mediante el lenguaje ensamblador MSIL\) muestra lo que podría provocar la advertencia CLS01512:  
  
```  
.method public specialname rtspecialname static vararg void  .cctor() cil managed  
```  
  
 Si se quita la palabra clave **vararg**, se puede resolver esta advertencia:  
  
```  
.method public specialname rtspecialname static void  .cctor() cil managed  
```