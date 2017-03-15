---
title: "Error del compilador CS0720 | Microsoft Docs"
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
  - "CS0720"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0720"
ms.assetid: 1a8e7613-6bfb-4178-a8b4-f4591316c0b8
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0720
'static class': no se pueden declarar indexadores en una clase estática  
  
 Los indexadores no son significativos en las clases estáticas, ya que solo se pueden usar con instancias y no es posible crear instancias de tipo estático.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS0720:  
  
```  
// CS0720.cs public static class Test { public int this[int index]  // CS0720 { get { return 1; } set {} } static void Main() {} }  
```