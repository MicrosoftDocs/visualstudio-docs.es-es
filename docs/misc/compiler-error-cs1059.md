---
title: "Error del compilador CS1059 | Microsoft Docs"
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
  - "CS1059"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1059"
ms.assetid: 3ebd02ab-e40d-4aad-b901-a0cb6e2eace7
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1059
El operando de un operador de incremento o decremento debe ser una variable, una propiedad o un indizador.  
  
 Este error se produce al intentar incrementar o disminuir un valor constante. También puede producirse si intenta incrementar una expresión como `(a+b)++`.  
  
### Para corregir este error  
  
-   Haga que la variable sea no constante.  
  
-   Quite el operador de incremento o disminución.  
  
-   Almacene la expresión en una variable, y luego incremente la variable.  
  
## Ejemplo  
 El ejemplo siguiente genera CS1059 porque `i` es una constante, no una variable, y `E` es un tipo `Enum`, cuyos elementos también son valores constantes.  
  
```  
// CS1059.cs class Program { public enum E : sbyte { a = 1, b = 2 } static void Main(string[] args) { const int i = 0; i++;            // CS1059 E test = E.a++; // CS1059 } }  
```  
  
## Vea también  
 [Constantes](/dotnet/csharp/programming-guide/classes-and-structs/constants)