---
title: "Error del compilador CS0677 | Microsoft Docs"
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
  - "CS0677"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0677"
ms.assetid: 6a4a3703-9b44-4c4f-a564-8b437b1cb6b8
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0677
'variable': un campo volátil no puede ser del tipo 'type'  
  
 Los campos que se declaran con la palabra clave `volatile` debe ser uno de los tipos siguientes:  
  
-   Cualquier tipo de referencia  
  
-   Cualquier tipo de puntero \(en un contexto `unsafe`\)  
  
-   Los tipos `sbyte`, **byte**, **short**, `ushort`, `int`, `uint`, `char`, **float**, `bool`  
  
-   Tipos de enumeración basados en alguno de los tipos anteriores  
  
 El ejemplo siguiente genera la advertencia CS0677:  
  
```  
// CS0677.cs class TestClass { private volatile long i;   // CS0677 public static void Main() { } }  
```