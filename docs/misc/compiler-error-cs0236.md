---
title: "Error del compilador CS0236 | Microsoft Docs"
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
  - "CS0236"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0236"
ms.assetid: 1522c421-744f-441f-9e05-6bb31311ab2a
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0236
Un inicializador de campo no puede hacer referencia al campo, método o propiedad no estáticos 'campo'.  
  
 Los campos de instancia no pueden usarse para inicializar otros campos de instancia fuera de un método. Si está intentando inicializar una variable fuera de un método, considere la posibilidad de realizar la inicialización dentro del constructor de clase. Para obtener más información, consulta [Métodos](/dotnet/csharp/programming-guide/classes-and-structs/methods).  
  
 El ejemplo siguiente genera la advertencia CS0236:  
  
```  
// CS0236.cs public class MyClass { public int i = 5; public int j = i;  // CS0236 public int k;      // initialize in constructor MyClass() { k = i; } public static void Main() { } }  
```