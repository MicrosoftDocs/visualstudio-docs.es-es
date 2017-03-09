---
title: "Error del compilador CS0514 | Microsoft Docs"
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
  - "CS0514"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0514"
ms.assetid: 74ce3010-f9e9-458c-8b68-cfb908a3e7a2
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0514
'constructor': el constructor estático no puede tener ninguna llamada de constructor 'this' o 'base' explícita  
  
 No se permite llamar a `this` en el constructor estático porque se llama automáticamente al constructor estático antes de crear cualquier instancia de la clase. Además, los constructores estáticos no se heredan y no se puede llamar directamente.  
  
 Para obtener más información, consulte [this](/dotnet/csharp/language-reference/keywords/this) y [base](/dotnet/csharp/language-reference/keywords/base).  
  
## Ejemplo  
 El ejemplo siguiente genera el error CS0514:  
  
```  
// CS0514.cs class A { static A() : base(0) // CS0514 { } public A(object o) { } } class B { static B() : this(null) // CS0514 { } public B(object o) { } }  
```