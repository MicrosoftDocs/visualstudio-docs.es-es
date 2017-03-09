---
title: "Error del compilador CS0633 | Microsoft Docs"
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
  - "CS0633"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0633"
ms.assetid: a24d310b-151a-45eb-b150-3407940ec24c
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0633
El argumento pasado al atributo 'attribute' debe ser un identificador válido  
  
 Cualquier argumento que se pase a los atributos <xref:System.Diagnostics.ConditionalAttribute> o <xref:System.Runtime.CompilerServices.IndexerNameAttribute> debe ser un identificador válido. Esto significa que no puede contener caracteres como "\+" que no sean válidos cuando aparecen en identificadores.  
  
## Ejemplo  
 En este ejemplo se muestra el error CS0633 con <xref:System.Diagnostics.ConditionalAttribute>. El ejemplo siguiente genera la advertencia CS0633.  
  
```  
// CS0633a.cs #define DEBUG using System.Diagnostics; public class Test { [Conditional("DEB+UG")]   // CS0633 // try the following line instead // [Conditional("DEBUG")] public static void Main() { } }  
```  
  
## Ejemplo  
 En este ejemplo se muestra el error CS0633 con <xref:System.Runtime.CompilerServices.IndexerNameAttribute>.  
  
```  
// CS0633b.cs // compile with: /target:module #define DEBUG using System.Runtime.CompilerServices; public class Test { [IndexerName("Invalid+Identifier")]   // CS0633 // try the following line instead // [IndexerName("DEBUG")] public int this[int i] { get { return i; } } }  
  
```