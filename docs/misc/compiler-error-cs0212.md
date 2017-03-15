---
title: "Error del compilador CS0212 | Microsoft Docs"
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
  - "CS0212"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0212"
ms.assetid: 1b8973b8-03c9-42a6-bf61-2e401b89387e
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0212
Solo se puede adquirir la dirección de una expresión de tipo unfixed de un inicializador de instrucción fixed  
  
 Para obtener más información, consulta [Código no seguro y punteros](/dotnet/csharp/programming-guide/unsafe-code-pointers/index).  
  
 En el ejemplo siguiente se muestra cómo obtener la dirección de una expresión sin corregir. El ejemplo siguiente genera la advertencia CS0212.  
  
```  
// CS0212a.cs // compile with: /unsafe /target:library public class A { public int iField = 5; unsafe public void M() { A a = new A(); int* ptr = &a.iField;   // CS0212 } // OK unsafe public void M2() { A a = new A(); fixed (int* ptr = &a.iField) {} } }  
```  
  
 El ejemplo siguiente también genera la advertencia CS0212 y se muestra cómo resolverlo:  
  
```  
// CS0212b.cs // compile with: /unsafe /target:library using System; public class MyClass { unsafe public void M() { // Null-terminated ASCII characters in an sbyte array sbyte[] sbArr1 = new sbyte[] { 0x41, 0x42, 0x43, 0x00 }; sbyte* pAsciiUpper = &sbArr1[0];   // CS0212 // To resolve this error, delete the previous line and // uncomment the following code: // fixed (sbyte* pAsciiUpper = sbArr1) // { //    String szAsciiUpper = new String(pAsciiUpper); // } } }  
```