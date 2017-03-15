---
title: "Error del compilador CS0439 | Microsoft Docs"
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
  - "CS0430"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0439"
ms.assetid: 5cbac869-1b1b-45f9-98c8-38c17348035f
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0439
La declaración de un alias externo debe preceder a los demás elementos definidos en el espacio de nombres  
  
 Este error se produce cuando una declaración `extern` viene detrás de otro elemento, como una declaración `using`, en el mismo espacio de nombres. Las declaraciones `extern` deben preceder a todos los demás elementos del espacio de nombres.  
  
## Ejemplo  
 El ejemplo siguiente genera el error CS0439:  
  
```  
// CS0439.cs using System; extern alias MyType;   // CS0439 // To resolve the error, make the extern alias the first line in the file. public class Test { public static void Main() { } }  
```