---
title: "Error del compilador CS0453 | Microsoft Docs"
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
  - "CS0453"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0453"
ms.assetid: a1bbd09e-6313-4bfd-84bf-bc15a8d214a6
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0453
El tipo 'Type Name' debe ser un tipo de valor que no acepte valores NULL para poder usarlo como el parámetro 'Parameter Name' en el tipo o método genéricos 'Generic Identifier'  
  
 Este error se produce cuando se utiliza un argumento de tipo sin valor en la creación de instancias de un tipo o un método genérico que tiene la restricción **value** en él. También puede producirse cuando se usa un argumento de tipo de valor que acepte valores NULL. Consulte las dos últimas líneas de código en el ejemplo siguiente.  
  
## Ejemplo  
 El código siguiente genera este error.  
  
```  
// CS0453.cs using System; public class HV<S> where S : struct { } public class H1 : HV<string> { }                   // CS0453 public class H2 : HV<H1> { }                       // CS0453 public class H3<S> : HV<S> where S : class { }     // CS0453 public class H4 : HV<int?> { }                     // CS0453 public class H5 : HV<Nullable<Nullable<int>>> { }  // CS0453  
```