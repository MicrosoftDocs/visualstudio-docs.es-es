---
title: "Error del compilador CS0176 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0176"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0176"
ms.assetid: 783c13d8-5ac3-4aeb-bd63-0468cb05550d
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0176
No se puede acceder al miembro estático 'miembro' con una referencia de instancia; califíquelo con un nombre de tipo en su lugar.  
  
 Solo puede usarse un nombre de clase para calificar una variable [estática](/dotnet/csharp/language-reference/keywords/static); un nombre de instancia no puede ser un calificador. Para obtener más información, consulta [Clases estáticas y sus miembros](/dotnet/csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members).  
  
 El ejemplo siguiente genera la advertencia CS0176:  
  
```  
// CS0176.cs public class MyClass2 { public static int num; } public class Test { public static void Main() { MyClass2 mc2 = new MyClass2(); int i = mc2.num;   // CS0176 // try the following line instead // int i = MyClass2.num; } }  
  
```