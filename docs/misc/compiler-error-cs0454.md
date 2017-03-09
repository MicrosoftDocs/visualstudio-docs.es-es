---
title: "Error del compilador CS0454 | Microsoft Docs"
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
  - "CS0454"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0454"
ms.assetid: 2c83bc5e-53bb-473e-92aa-5122dadd79d1
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0454
Dependencia de restricción circular que requiere 'Parámetro de tipo 1' y 'Parámetro de tipo 2'  
  
 Este error se produce porque, en algún punto, un parámetro de tipo hace referencia a un segundo parámetro que, a su vez, hace referencia al primero. Para corregir este error, interrumpa la dependencia circular quitando una de las restricciones. Tenga en cuenta que la dependencia de restricción circular puede ser indirecta.  
  
## Ejemplo  
 El código siguiente genera el error CS0454.  
  
```  
// CS0554 using System; public class GenericsErrors { public class G4<T> where T : T { } // CS0454 }  
```  
  
## Ejemplo  
 En el ejemplo siguiente se muestra una dependencia circular entre dos restricciones de tipo.  
  
```  
public class Gen<T,U> where T : U where U : T  // CS0454 { }  
```