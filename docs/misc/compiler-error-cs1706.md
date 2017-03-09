---
title: "Error del compilador CS1706 | Microsoft Docs"
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
  - "CS1706"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1706"
ms.assetid: 8c589a49-3959-422e-ac18-65a2eaae3da0
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1706
La expresión no puede contener métodos anónimos ni expresiones lambda.  
  
 No se puede insertar un método anónimo dentro de una expresión.  
  
### Para corregir este error  
  
1.  Use un `delegate` normal en la expresión.  
  
## Ejemplo  
 El ejemplo siguiente genera el error CS1706.  
  
```  
// CS1706.cs using System; delegate void MyDelegate(); class MyAttribute : Attribute { public MyAttribute(MyDelegate d) { } } // Anonymous Method in Attribute declaration is not allowed. [MyAttribute(delegate{/* anonymous Method in Attribute declaration */})]  // CS1706 class Program { }  
```