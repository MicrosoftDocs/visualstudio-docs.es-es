---
title: "Error del compilador CS1730 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1730"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1730"
ms.assetid: 20900ca0-702f-4f35-9a60-2dee9cb11902
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1730
Los atributos de módulo y ensamblado deben ir delante de los demás elementos definidos en un archivo, excepto las cláusulas using y las declaraciones de alias externos.  
  
 Un atributo que se aplica en el nivel de ensamblado no puede aparecer después de ninguna definición de tipo.  
  
### Para corregir este error  
  
1.  Mueva el atributo al principio del archivo, pero por debajo de las directivas `using` y la declaraciones de alias `extern`.  
  
## Ejemplo  
 El código siguiente genera el error CS1730:  
  
```  
// cs1730.cs class Test { } [assembly: System.Attribute] // CS1730  
```  
  
## Vea también  
 [Atributos](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)