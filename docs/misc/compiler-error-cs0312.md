---
title: "Error del compilador CS0312 | Microsoft Docs"
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
  - "CS0312"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0312"
ms.assetid: 552db0ae-2ecf-4beb-9606-bbe58e5708f6
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0312
El tipo 'tipo1' no se puede usar como parámetro de tipo 'nombre' en el tipo o método genérico 'nombre'. El tipo que acepta valores NULL 'tipo1' no satisface la restricción de 'tipo2'.  
  
 Un tipo que acepta valores NULL es distinto de su homólogo que no acepta valores NULL; no existe una conversión de referencia implícita ni conversión de identificación entre ellos. Una conversión boxing que acepta valores NULL no satisface una restricción de tipo genérico. En el ejemplo siguiente, el primer parámetro de tipo es un `Nullable<int>` y el segundo parámetro de tipo es un `System.Int32`.  
  
### Para corregir este error  
  
1.  Quite la restricción.  
  
2.  En el ejemplo siguiente, el segundo argumento de tipo es `int?` o `object`.  
  
## Ejemplo  
 El código siguiente genera CS0312:  
  
```  
// cs0312.cs class Program { static void MTyVar<T, U>() where T : U { } static int Main() { MTyVar<int?, int>(); // CS0312 return 1; } }  
```  
  
 Aunque un tipo que acepta valores NULL es distinto de un tipo que no acepta valores NULL, se permiten varios tipos de conversiones entre los valores que aceptan valores NULL y los que no los aceptan.  
  
## Vea también  
 [Tipos que aceptan valores NULL](/dotnet/csharp/programming-guide/nullable-types/index)