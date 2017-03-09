---
title: "Advertencia del compilador (nivel 3) CS0414 | Microsoft Docs"
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
  - "CS0414"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0414"
ms.assetid: 6a0a80be-799b-4d9c-a7e0-6b91e9ce7be0
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 3) CS0414
El campo privado 'field' está asignado, pero su valor nunca se usa  
  
 Esta advertencia puede producirse en varios escenarios en los que el compilador puede comprobar que nunca se hace referencia a una variable:  
  
-   Se asigna un valor constante a un campo privado, pero después nunca se lee. Esta asignación innecesaria puede afectar al rendimiento. Considere la posibilidad de quitar el campo.  
  
-   A un campo estático privado o interno solo se le asigna un valor constante en el inicializador. Considere la posibilidad de cambiar el campo por un elemento const.  
  
-   Se asignan valores constantes a un campo privado o interno y solo se utiliza en los bloques que se excluyen mediante directivas \#ifdef. Considere la posibilidad de colocar el campo dentro del bloque \#ifdef.  
  
-   Se asignan valores constantes a un campo privado o interno en varias ubicaciones, pero no se accede a él de otra forma. Si no necesita el campo, considere la posibilidad de eliminarlo. De lo contrario, úselo de manera adecuada.  
  
 En otras situaciones o si la solución recomendada no es aceptable, utilice \#pragma 0414.  
  
 En el ejemplo siguiente se muestra una manera en que se generará la advertencia CS0414:  
  
```  
// CS0414 // compile with: /W3 class C { private int i = 1;  // CS0414 public static void Main() { } }  
```  
  
 **Nota** Si la variable `i` se declara como `protected or public`, no se generará ningún error porque el compilador no puede saber si una clase derivada podría utilizarla o algún otro código de cliente puede crear una instancia de la clase y hacer referencia a la variable  
  
## Vea también  
 [C\# Compiler Errors](/dotnet/csharp/language-reference/compiler-messages/index)   
 [C\# Compiler Options](/dotnet/csharp/language-reference/compiler-options/index)