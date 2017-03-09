---
title: "Error del compilador CS0438 | Microsoft Docs"
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
  - "CS0438"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0438"
ms.assetid: 92c91ecb-8d6a-4850-84eb-c095c3c957f1
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0438
El tipo 'tipo' en el 'módulo\_1' está en conflicto con el espacio de nombres 'espacio de nombres' en el 'módulo\_2'.  
  
 Este error se produce cuando un tipo en un archivo de origen entra en conflicto con un espacio de nombres en otro archivo de origen. Esto suele suceder cuando uno o ambos provienen de un módulo agregado. Para solucionarlo, cambie el nombre del tipo o del espacio de nombres que produjo el conflicto.  
  
 El ejemplo siguiente genera el error CS0438:  
  
 Compile este archivo primero:  
  
```  
// CS0438_1.cs // compile with: /target:module public class Util { public class A { } }  
```  
  
 A continuación, compile este archivo:  
  
```  
// CS0438_2.cs // compile with: /target:module namespace Util { public class A { } }  
```  
  
 Y luego compile este archivo:  
  
```  
// CS0438_3.cs // compile with: /addmodule:CS0438_1.netmodule /addmodule:CS0438_2.netmodule using System; public class Test { public static void Main() { Console.WriteLine(typeof(Util.A));   // CS0438 } }  
  
```