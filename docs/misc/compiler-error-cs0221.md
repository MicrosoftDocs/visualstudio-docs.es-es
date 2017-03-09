---
title: "Error del compilador CS0221 | Microsoft Docs"
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
  - "CS0221"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0221"
ms.assetid: 97170b49-54f1-4dac-a865-2f9cc6bf55b1
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0221
El valor constante 'valor' no se puede convertir en 'tipo' \(use la sintaxis 'unchecked' para invalidar el valor\)  
  
 Una operación de asignación que tendría como resultado una pérdida de datos fue detectada por el modo [checked](/dotnet/csharp/language-reference/keywords/checked), que está activado de forma predeterminada. Corrija la asignación o use el modo [unchecked](/dotnet/csharp/language-reference/keywords/unchecked) para resolver este error. Para obtener más información, consulte [Checked y unchecked](/dotnet/csharp/language-reference/keywords/checked-and-unchecked).  
  
 El ejemplo siguiente genera la advertencia CS0221:  
  
```  
// CS0221.cs public class MyClass { public static void Main() { // unchecked // { int a = (int)0xFFFFFFFF;   // CS0221 a++; // } } }  
```