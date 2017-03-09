---
title: "Error del compilador CS1665 | Microsoft Docs"
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
  - "CS1665"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1665"
ms.assetid: 93d4a4af-23c3-4730-a778-77852e41db4d
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1665
Los búferes de tamaño fijo deben tener una longitud mayor que cero  
  
 Este error se produce si se declara un búfer de tamaño fijo con un cero o tamaño negativo. La longitud de un búfer de tamaño fijo debe ser un entero positivo.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS1665.  
  
```  
// CS1665.cs // compile with: /unsafe /target:library struct S { public unsafe fixed int A[0];   // CS1665 }  
```