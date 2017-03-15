---
title: "Error del compilador CS1671 | Microsoft Docs"
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
  - "CS1671"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1671"
ms.assetid: 34255d2b-6ff6-4ac1-b617-3199e16726cf
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1671
Una declaración de espacio de nombres no puede tener modificadores ni atributos  
  
 Los modificadores no son significativos cuando se aplican a un espacio de nombres y, por tanto, no se admiten.  
  
 El ejemplo siguiente genera la advertencia CS1671:  
  
```  
// CS1671.cs public namespace NS // CS1671 { }  
```