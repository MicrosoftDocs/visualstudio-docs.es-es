---
title: "Error del compilador CS1955 | Microsoft Docs"
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
  - "CS1955"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1955"
ms.assetid: 38a8542d-da53-4739-b807-46c8c077363c
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1955
No se puede utilizar como método el miembro no invocable 'name'.  
  
 Solo se pueden invocar métodos y delegados. Este error se genera cuando se intentan utilizar paréntesis vacíos para llamar a un valor distinto de un método o un delegado.  
  
### Para corregir este error  
  
1.  Quite los paréntesis de la expresión.  
  
## Ejemplo  
 El código siguiente genera el error CS1955 porque el código intenta invocar un campo y una propiedad mediante el operador de llamada a método [\(\)](/dotnet/csharp/language-reference/operators/invocation-operator). No puede llamar a un campo ni una propiedad, pero puede acceder al valor que almacena con el operador de acceso a miembro \( [.](/dotnet/csharp/language-reference/operators/member-access-operator) \).  
  
```  
// cs1955.cs class A { public int x = 0; public int X { get { return x; } set { x = value; } } } class Test { static int Main() { A a = new A(); a.x(); // CS1955 a.X(); // CS1955 // Try this line instead: // int num = a.x; } }  
```