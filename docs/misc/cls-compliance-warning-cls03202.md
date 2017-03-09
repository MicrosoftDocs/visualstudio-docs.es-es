---
title: "Advertencia de conformidad con CLS CLS03202 | Microsoft Docs"
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
  - "CLS03202"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS03202"
ms.assetid: 2219c86c-9276-4244-a2ff-bce578c4d65f
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Advertencia de conformidad con CLS CLS03202
Los métodos add y remove de un evento deben tomar un parámetro cuyo tipo defina el tipo del evento, y ese tipo debe derivarse de System.Delegate.  
  
 Los métodos add y remove de un evento deben tomar un parámetro cuyo tipo defina el tipo del evento, y ese tipo debe derivarse de System.Delegate.  
  
 Para más información sobre la comprobación de conformidad con CLS, vea [CLS Compliant Assemblies](http://msdn.microsoft.com/es-es/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 La siguiente declaración de función \(mediante el lenguaje ensamblador MSIL\) muestra lo que podría provocar la advertencia CLS03202:  
  
```  
// bad .method public specialname instance void add_MyEvent(class MyDelegate __unnamed000, int32 __extra) cil managed {}  
```  
  
 Puede resolver esta advertencia si el descriptor de acceso de eventos solo toma un parámetro:  
  
```  
.method public specialname instance void add_MyEvent(class MyDelegate __unnamed000) cil managed {}  
```