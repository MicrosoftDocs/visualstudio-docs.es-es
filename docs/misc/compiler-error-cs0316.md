---
title: "Error del compilador CS0316 | Microsoft Docs"
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
  - "CS0316"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0316"
ms.assetid: 8b70abbe-dd4f-473f-8dfe-f8309abef276
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0316
El nombre de parámetro 'nombre' entra en conflicto con un nombre de parámetro generado automáticamente  
  
 No se pueden usar palabras reservadas como nombres de parámetros. En el ejemplo siguiente, `value` es una palabra reservada en el contexto de un descriptor de acceso de indexador o propiedad predeterminada.  
  
### Para corregir este error  
  
1.  Cambie el nombre del parámetro.  
  
## Ejemplo  
 El código siguiente genera el error CS0316:  
  
```  
// cs0316.cs // Compile with: /target:library public class Test { public int this[int value] // CS0316 { get { return 1; } set { } } }  
```  
  
## Vea también  
 [Indizadores](/dotnet/csharp/programming-guide/indexers/index)   
 [Palabras clave de C\#](/dotnet/csharp/language-reference/keywords/index)