---
title: "Error del compilador CS0075 | Microsoft Docs"
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
  - "CS0075"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0075"
ms.assetid: 5084d260-705e-4ff5-8f7a-7f74052fcbbb
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0075
Para convertir un valor negativo, el valor debe ir entre paréntesis  
  
 Si realiza la conversión mediante una palabra clave que identifica un tipo predefinido, no son necesarios los paréntesis. De lo contrario, debe colocar los paréntesis porque \(x\) – y no se considerará una expresión de conversión. De la especificación C\#, sección 7.6.6:  
  
 *De la regla de desambiguación se deduce que, si x e y son identificadores, \(x\)y, \(x\)\(y\) y \(x\)\(\-y\) son expresiones de conversión, pero \(x\)\-y no, aunque x identifique un tipo. Sin embargo, si x es una palabra clave que identifica un tipo predefinido \(como int\), entonces las cuatro formas son expresiones de conversión \(porque esta palabra clave no puede ser una expresión por sí misma\).*  
  
 El código siguiente genera el error CS0075:  
  
```  
// CS0075 namespace MyNamespace { enum MyEnum { } public class MyClass { public static void Main() { // To fix the error, place the negative // values below in parentheses int i = (System.Int32) - 4; //CS0075 MyEnum e = (MyEnum) - 1;    //CS0075 System.Console.WriteLine(i); //to avoid warning System.Console.WriteLine(e); //to avoid warning } } }  
```  
  
## Vea también  
 [Conversiones de tipos](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)