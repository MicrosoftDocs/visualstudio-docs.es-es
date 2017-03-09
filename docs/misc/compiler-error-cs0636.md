---
title: "Error del compilador CS0636 | Microsoft Docs"
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
  - "CS0636"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0636"
ms.assetid: 47597f89-fbe6-4708-9493-3c86c6f0ce56
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0636
El atributo FieldOffset solo se puede colocar en miembros de tipos marcados con StructLayout\(LayoutKind.Explicit\)  
  
 Debe usar el atributo **StructLayout \(LayoutKind.Explicit\)** en la declaración struct, si contiene algún miembro marcado con el atributo **FieldOffset**. Para obtener más información, vea [FieldOffset](frlrfsystemruntimeinteropservicesfieldoffsetattributeclasstopic).  
  
 El ejemplo siguiente genera la advertencia CS0636:  
  
```  
// CS0636.cs using System; using System.Runtime.InteropServices; // To resolve the error, uncomment the following line: // [StructLayout(LayoutKind.Explicit)] struct Worksheet { [FieldOffset(4)]public int i;   // CS0636 } public class MainClass { public static void Main () { } }  
```