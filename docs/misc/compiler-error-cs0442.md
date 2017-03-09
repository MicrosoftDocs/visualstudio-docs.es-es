---
title: "Error del compilador CS0442 | Microsoft Docs"
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
  - "CS0442"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0442"
ms.assetid: a411660d-0db6-4b63-b19e-f4538fc201e5
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0442
'Property': las propiedades abstractas no pueden tener descriptores de acceso privados  
  
 Este error se produce cuando se usa el modificador de acceso "private" para modificar un descriptor de acceso abstracto. Para resolver, use un modificador de acceso distinto o convierta la propiedad en no abstracta.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS0442:  
  
```  
// CS0442.cs public abstract class MyClass { public abstract int AbstractProperty { get; private set;   // CS0442 // Try this instead: // set; } }  
```