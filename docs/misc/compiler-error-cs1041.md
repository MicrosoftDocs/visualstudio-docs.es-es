---
title: "Error del compilador CS1041 | Microsoft Docs"
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
  - "CS1041"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1041"
ms.assetid: 9f62c058-cd28-4cb5-835c-d0f25f4fd08e
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1041
Se esperaba un identificador, 'keyword' es una palabra clave  
  
 Se encontró una palabra reservada del lenguaje C\# donde se esperaba un identificador. Reemplace la [palabra clave](/dotnet/csharp/language-reference/keywords/index) por un identificador especificado por el usuario.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS1041:  
  
```  
// CS1041a.cs class MyClass { public void f(int long)   // CS1041 // Try the following instead: // public void f(int i) { } public static void Main() { } }  
```  
  
## Ejemplo  
 Cuando se importa desde otro lenguaje de programación que no tiene el mismo conjunto de palabras reservadas, puede modificar el identificador reservado con el prefijo @, como se muestra en el ejemplo siguiente.  
  
 Un identificador con un prefijo `@` se conoce como un identificador textual.  
  
```  
// CS1041b.cs class MyClass { public void f(int long)   // CS1041 // Try the following instead: // public void f(int @long) { } public static void Main() { } }  
```