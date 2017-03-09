---
title: "Advertencia del compilador (nivel 3) CS1717 | Microsoft Docs"
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
  - "CS1717"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1717"
ms.assetid: 5b150a2c-5d61-4cd8-b4d4-e6c2b93b52c6
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 3) CS1717
Asignación a la misma variable. ¿Quería asignar otro elemento?  
  
 Esta advertencia se produce cuando se asigna una variable a sí misma, por ejemplo: `a = a`.  
  
 Existen varios errores comunes que pueden generar esta advertencia:  
  
-   Escribir `a = a` como la condición de una instrucción **if**, por ejemplo: `if (a = a)`. Es probablemente que se quiera decir `if (a == a)`, que es siempre true. en este caso resulta más conciso escribirlo como `if (true)`.  
  
-   Error tipográfico. Probablemente se quiera decir `a = b`.  
  
-   En un constructor donde el parámetro tiene el mismo nombre que el campo, no debe usarse la palabra clave **this**. Es probable que se quiera decir `this.a = a`.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS1717.  
  
```  
// CS1717.cs // compile with: /W:3 public class Test { public static void Main() { int x = 0; x = x;   // CS1717 } }  
```