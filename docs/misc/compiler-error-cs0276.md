---
title: "Error del compilador CS0276 | Microsoft Docs"
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
  - "CS0276"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0276"
ms.assetid: 0c49017f-c7a9-42a5-9d0a-6f1d82142bd7
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0276
'property\/indexer': solo se pueden utilizar modificadores de accesibilidad en descriptores de acceso si la propiedad o indizador tiene tanto un descriptor de acceso get como set  
  
 Este error se produce cuando se declara una propiedad o un indizador con un solo descriptor de acceso y se usa un modificador de acceso en el descriptor de acceso. Para solucionarlo, quite el modificador de acceso o agregue otro descriptor de acceso.  
  
## Ejemplo  
 El ejemplo siguiente genera el error CS0276:  
  
```  
// CS0276.cs public class MyClass { public int Property { protected set { }   // CS0276 } public int Property2 { internal get { }   // CS0276 } }  
```