---
title: "Advertencia del compilador (nivel 1) CS0657 | Microsoft Docs"
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
  - "CS0657"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0657"
ms.assetid: d12d2efc-f44e-40e6-b825-5a66ead0c08e
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 1) CS0657
'attribute modifier' no es una ubicación de atributo válida para esta declaración. Las ubicaciones de atributo válidas para esta declaración son 'locations'. Todos los atributos de este bloque se omitirán.  
  
 El compilador encontró un modificador de atributo en una ubicación no válida. Vea [Destinos de atributo](http://msdn.microsoft.com/es-es/59a261f0-1cfb-4aa5-b610-6b735389882c) para más información.  
  
 El ejemplo siguiente genera la advertencia CS0657:  
  
```  
// CS0657.cs // compile with: /target:library public class TestAttribute : System.Attribute {} [return: Test]   // CS0657 return not valid on a class class Class1 {}  
```