---
title: "Error del compilador CS1959 | Microsoft Docs"
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
  - "CS1959"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1959"
ms.assetid: 20a31619-3e30-446a-becc-a7f8cfcec66d
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1959
'name' es de tipo 'type'. El tipo especificado en una declaración de constantes debe ser sbyte, byte, short, ushort, int, uint, long, ulong, char, float, double, decimal, bool, string, un tipo de enumeración o un tipo de referencia.  
  
 Los tipos permitidos en una declaración const se limitan a las descritas en este mensaje.  
  
### Para corregir este error  
  
1.  Declare la constante con un tipo permitido.  
  
## Ejemplo  
 El código siguiente genera el error CS1959 porque `null` no es un tipo.  
  
```  
// cs1959.cs class Program { static void Test<T>() where T : class { const T x = null; // CS1959 } }  
```  
  
## Vea también  
 [Constantes](/dotnet/csharp/programming-guide/classes-and-structs/constants)   
 [null](/dotnet/csharp/language-reference/keywords/null)