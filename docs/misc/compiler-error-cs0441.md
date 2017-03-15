---
title: "Error del compilador CS0441 | Microsoft Docs"
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
  - "CS0441"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0441"
ms.assetid: 3f07500a-d479-424c-a0f4-c219be1b5a45
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0441
'class': una clase no puede ser static y sealed  
  
 Este error se produce cuando se declara una clase que es static y sealed. Las clases estáticas son sealed por definición, por lo que no es necesario el modificador sealed. Para resolver, use solo un modificador.  
  
 El ejemplo siguiente genera el error CS0441:  
  
```  
// CS0441.cs sealed static class MyClass { }   // CS0441  
```