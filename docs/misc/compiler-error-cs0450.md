---
title: "Error del compilador CS0450 | Microsoft Docs"
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
  - "CS0450"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0450"
ms.assetid: 8eb0e98b-d7a1-49a7-8e55-36e2eb0057ff
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0450
'Nombre de parámetro de tipo': no se puede especificar una clase de restricción y la restricción 'class' o 'struct'.  
  
 Si un parámetro de tipo está restringido por la restricción de tipo estructura, resulta contradictorio que también esté restringido por un tipo de clase concreto, puesto que las estructuras y clases son categorías mutuamente excluyentes. Si un parámetro de tipo está restringido por una restricción de tipo de clase específica, por definición está restringido por la restricción de tipo de clase, por lo que especificar la restricción de tipo de clase es redundante.  
  
## Ejemplo  
  
```  
// CS0450.cs // compile with: /t:library public class GenericsErrors { public class B { } public class G3<T> where T : struct, B { } // CS0450 // To resolve, use the following line instead: // public class G3<T> where T : B { } }  
```