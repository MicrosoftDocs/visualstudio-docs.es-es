---
title: "Error del compilador CS0241 | Microsoft Docs"
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
  - "CS0241"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "valores predeterminados de parámetros de método"
  - "valores predeterminados, valores de parámetros"
  - "valores predeterminados, valores de parámetros de método"
  - "valores de parámetros predeterminados"
  - "CS0241"
ms.assetid: be31b194-3de5-4aab-b23a-6cf790f940ab
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0241
No se permiten especificadores de parámetros predeterminados  
  
 Los [parámetros de método](/dotnet/csharp/language-reference/keywords/method-parameters) no pueden tener valores predeterminados. Use sobrecargas de métodos si desea conseguir el mismo efecto. Para obtener más información, consulta [Pasar parámetros](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters).  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS0241: Además, en el ejemplo se muestra cómo simular, con sobrecarga, un método con argumentos predeterminados.  
  
```  
// CS0241.cs public class A { public void Test(int i = 9) {}   // CS0241 } public class B { public void Test() { Test(9); } public void Test(int i)  {} } public class C { public static void Main() { B x = new B(); x.Test(); } }  
```