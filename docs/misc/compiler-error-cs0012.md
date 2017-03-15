---
title: "Error del compilador CS0012 | Microsoft Docs"
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
  - "CS0012"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0012"
ms.assetid: 5523e349-22f4-4b0b-b4b0-c4bf26c461f4
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0012
El tipo 'tipo' está definido en un ensamblado al que no se hace referencia. Debe agregar una referencia al ensamblado 'ensamblado'.  
  
 No se encontró la definición de un tipo al que se hace referencia. Esto puede ocurrir si un archivo .DLL necesario no se incluye en la compilación. Para obtener más información, consulte [Add Reference Dialog Box](http://msdn.microsoft.com/es-es/2feb0fe2-0805-4cc9-8cba-b0315849dfb7) y [\/reference \(Import Metadata\)](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option).  
  
 La siguiente secuencia de compilaciones dará como resultado CS0012:  
  
```  
// cs0012a.cs // compile with: /target:library public class A {}  
```  
  
 Entonces:  
  
```  
// cs0012b.cs // compile with: /target:library /reference:cs0012a.dll public class B { public static A f() { return new A(); } }  
```  
  
 Entonces:  
  
```  
// cs0012c.cs // compile with: /reference:cs0012b.dll class C { public static void Main() { object o = B.f();   // CS0012 } }  
```  
  
 Se puede resolver el error CS0012 compilando con `/reference:cs0012b.dll;cs0012a.dll`, o en Visual Studio mediante el [Add Reference Dialog Box](http://msdn.microsoft.com/es-es/2feb0fe2-0805-4cc9-8cba-b0315849dfb7) para agregar una referencia a cs0012a.dll además de cs0012b.dll.