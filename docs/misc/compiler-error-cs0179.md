---
title: "Error del compilador CS0179 | Microsoft Docs"
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
  - "CS0179"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0179"
ms.assetid: bef000ca-64d7-4809-b2a0-de6927b04b0d
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0179
'member' no puede ser extern y declarar un cuerpo  
  
 Cuando se marca un miembro de clase [extern](/dotnet/csharp/language-reference/keywords/extern), significa que su definición se encuentra en otro archivo. Por lo tanto, un miembro de clase marcado como **extern** no se pueden definir en la clase. Quite la palabra clave `extern` o elimine la definición. Para obtener más información, consulta [Métodos](/dotnet/csharp/programming-guide/classes-and-structs/methods).  
  
 El ejemplo siguiente genera la advertencia CS0179:  
  
```  
// CS0179.cs public class MyClass { public extern int ExternMethod(int aa)   // CS0179 { return 0; } // try the following line instead // public extern int ExternMethod(int aa); public static void Main() { } }  
```