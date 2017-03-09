---
title: "Error del compilador CS0644 | Microsoft Docs"
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
  - "CS0644"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0644"
ms.assetid: 835f3ee2-f897-4ba2-ad13-af629a9ab7fe
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0644
'class1' no se puede derivar de la clase especial 'class2'  
  
 Las clases no pueden heredar explícitamente de ninguna de las clases base siguientes:  
  
-   **System.Enum**  
  
-   **System.ValueType**  
  
-   **System.Delegate**  
  
-   **System.Array**  
  
 El compilador las usa como clases base implícitas. Por ejemplo, **System.ValueType** es la clase base implícita de las estructuras.  
  
 El ejemplo siguiente genera la advertencia CS0644:  
  
```  
// CS0644.cs class MyClass : System.ValueType   // CS0644 { }  
```