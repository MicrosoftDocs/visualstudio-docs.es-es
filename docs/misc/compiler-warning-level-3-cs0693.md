---
title: "Advertencia del compilador (nivel 3) CS0693 | Microsoft Docs"
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
  - "CS0693"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0693"
ms.assetid: a3902336-49db-4808-b41f-8f0936bff53a
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 3) CS0693
El parámetro de tipo 'type parameter' tiene el mismo nombre que el parámetro de tipo de un tipo externo 'type'  
  
 Este error se produce cuando tiene un miembro genérico, como un método dentro de una clase genérica. Como el parámetro de tipo del método no es necesariamente el mismo que el de la clase, no puede asignarles el mismo nombre. Para obtener más información, consulta [Métodos genéricos](/dotnet/csharp/programming-guide/generics/generic-methods).  
  
 Para evitar esta situación, utilice un nombre diferente para uno de los parámetros de tipo.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS0693.  
  
```  
// CS0693.cs // compile with: /W:3 /target:library class Outer<T> { class Inner<T> {}   // CS0693 // try the following line instead // class Inner<U> {} }  
```