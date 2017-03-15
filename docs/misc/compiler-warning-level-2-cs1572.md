---
title: "Advertencia del compilador (nivel 2) CS1572 | Microsoft Docs"
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
  - "CS1572"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1572"
ms.assetid: 24bc8b96-29d2-4201-bc4e-6b9b5a4f5a1d
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 2) CS1572
El comentario XML en 'construct' tiene una etiqueta de parámetro para 'parámetro', pero no hay ningún parámetro con ese nombre.  
  
 Al usar la opción de compilador [\/doc](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option), se especificó un comentario para un parámetro que no existe para el método. Cambie el valor pasado al atributo de nombre o quite una de las líneas de comentario.  
  
 El ejemplo siguiente genera la advertencia CS1572:  
  
```  
// CS1572.cs // compile with: /W:2 /doc:x.xml /// <summary>help text</summary> public class MyClass { /// <param name='Int1'>Used to indicate status.</param> /// <param name='Char1'>Used to indicate status.</param> /// <param name='Char2'>???</param> // CS1572 public static void MyMethod(int Int1, char Char1) { } /// <summary>help text</summary> public static void Main () { } }  
```