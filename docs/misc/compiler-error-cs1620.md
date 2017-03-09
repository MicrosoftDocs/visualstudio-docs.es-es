---
title: "Error del compilador CS1620 | Microsoft Docs"
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
  - "CS1620"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1620"
ms.assetid: 13933976-218a-4fe2-8fde-5b9af522e2e5
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1620
Se debe pasar el argumento 'number' con la palabra clave 'keyword'.  
  
 Este error se produce si se pasa un argumento a una función que toma un parámetro [ref](/dotnet/csharp/language-reference/keywords/ref) o [out](/dotnet/csharp/language-reference/keywords/out) y no incluye la palabra clave `ref` o `out` en el momento de la llamada, o bien incluye la palabra clave incorrecta. El texto del error indica la palabra clave adecuada para usarse y el argumento que produjo el error.  
  
 El ejemplo siguiente genera la advertencia CS1620:  
  
```  
// CS1620.cs class C { void f(ref int i) {} public static void Main() { int x = 1; f(out x);  // CS1620 – f takes a ref parameter, not an out parameter // Try this line instead: // f(ref x); } }  
```