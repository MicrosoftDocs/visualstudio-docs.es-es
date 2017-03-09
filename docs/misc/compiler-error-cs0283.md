---
title: "Error del compilador CS0283 | Microsoft Docs"
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
  - "CS0283"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0283"
ms.assetid: f94a5b84-92c5-4602-894d-6f856d57e0e6
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0283
El tipo 'type' no se puede declarar const  
  
 El tipo especificado en una declaración de constante debe ser `byte`, `char`, `short`, `int`, `long`, `float`, `double`, `decimal`, `bool`, `string`, un tipo de enumeración o un tipo de referencia que tenga asignado un valor null. Cada expresión constante debe generar un valor del tipo de destino o de un tipo que pueda convertirse al tipo de destino mediante conversión implícita.  
  
## Ejemplo  
 El siguiente ejemplo genera el error CS0283.  
  
```  
// CS0283.cs struct MyTest { } class MyClass { // To resolve the error but retain the "const-ness", // change const to readonly. const MyTest test = new MyTest();   // CS0283 public static int Main() { return 1; } }  
```