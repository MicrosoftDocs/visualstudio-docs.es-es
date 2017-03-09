---
title: "Advertencia del compilador (nivel 1) CS1581 | Microsoft Docs"
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
  - "CS1581"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1581"
ms.assetid: b7ac7586-a724-492c-887f-795af1c3bcc4
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 1) CS1581
Tipo de valor devuelto no válido en el atributo cref del comentario XML  
  
 Al intentar hacer referencia a un método, el compilador detectó un error debido a un tipo de valor devuelto no válido.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS1581:  
  
```  
// CS1581.cs // compile with: /W:1 /doc:x.xml /// <summary>help text</summary> public class MyClass { /// <summary>help text</summary> public static void Main() { } /// <summary>help text</summary> public static explicit operator int(MyClass f) { return 0; } } /// <seealso cref="MyClass.explicit operator intt(MyClass)"/>  // CS1581 // try the following line instead // /// <seealso cref="MyClass.explicit operator int(MyClass)"/> public class MyClass2 { }  
```