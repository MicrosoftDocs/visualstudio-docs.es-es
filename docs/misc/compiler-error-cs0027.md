---
title: "Error del compilador CS0027 | Microsoft Docs"
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
  - "CS0027"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0027"
ms.assetid: 3a599876-9643-4c68-9457-3306858a73e9
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0027
La palabra clave 'this' no está disponible en el contexto actual  
  
 La palabra clave [this](/dotnet/csharp/language-reference/keywords/this) se encuentra fuera de una propiedad, un método o un constructor.  
  
 Para corregir este error, modifique la instrucción para eliminar el uso de la palabra clave `this` y\/o mueva parte de la instrucción, o su totalidad, dentro de una propiedad, un método o un constructor.  
  
 El ejemplo siguiente genera el error CS0027:  
  
```  
using System; using System.Collections.Generic; using System.Text; namespace ConsoleApplication3 { class MyClass { int err1 = this.Fun() + 1;  // CS0027 public int Fun() { return 10; } public void Test() { // valid use of this int err = this.Fun() + 1; Console.WriteLine(err); } public static void Main() { MyClass c = new MyClass(); c.Test(); } } }  
```