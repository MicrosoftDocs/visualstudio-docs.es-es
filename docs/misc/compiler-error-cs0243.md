---
title: "Error del compilador CS0243 | Microsoft Docs"
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
  - "CS0243"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0243"
ms.assetid: 2506e4cb-dc26-46b4-a58c-ab6bf1601144
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0243
El atributo Conditional no es válido en 'método' porque es un método de invalidación.  
  
 El atributo [Conditional](http://msdn.microsoft.com/es-es/e1c4913b-74d0-421a-8a6d-c14b3f0e68fb) no se permite en un método marcado con la palabra clave [override](/dotnet/csharp/language-reference/keywords/override). Para obtener más información, consulta [Saber cuándo utilizar las palabras clave Override y New](/dotnet/csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords).  
  
 El compilador nunca se enlaza a métodos de invalidación; solo se enlaza al método base y Common Language Runtime llama a la invalidación, según corresponda.  
  
 El ejemplo siguiente genera la advertencia CS0243:  
  
```  
// CS0243.cs // compile with: /target:library public class MyClass { public virtual void M() {} } public class MyClass2 : MyClass { [System.Diagnostics.ConditionalAttribute("MySymbol")]   // CS0243 // remove Conditional attribute or remove override keyword public override void M() {} }  
```