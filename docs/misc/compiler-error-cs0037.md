---
title: "Error del compilador CS0037 | Microsoft Docs"
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
  - "CS0037"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0037"
ms.assetid: 1d34a71e-10a0-4fa8-9b94-343e69428c61
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0037
No se puede convertir null a 'type' porque es un tipo de valor que no acepta valores Null  
  
 El compilador no puede asignar null a un tipo de valor; null sólo puede asignarse a un [tipo de referencia](/dotnet/csharp/language-reference/keywords/reference-types) o a un tipo que acepte valores Null.[struct](/dotnet/csharp/language-reference/keywords/struct) es un tipo de valor. Para obtener más información, consulta [Tipos que aceptan valores NULL](/dotnet/csharp/programming-guide/nullable-types/index).  
  
 El ejemplo siguiente genera la advertencia CS0037:  
  
```  
// CS0037.cs public struct s { } class a { public static void Main() { int i = null;   // CS0037 s ss = null;    // CS0037 } }  
```