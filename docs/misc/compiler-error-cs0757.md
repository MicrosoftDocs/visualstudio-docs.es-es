---
title: "Error del compilador CS0757 | Microsoft Docs"
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
  - "CS0757"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0757"
ms.assetid: ba093570-306d-4b7b-aad5-1a3855ad6776
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0757
Un método parcial no puede tener varias declaraciones de implementación.  
  
 Un método parcial consta exactamente de una declaración de definición \(firma\) y una o ninguna declaración de implementación opcional \(cuerpo\). No se permiten varias declaraciones de implementación para las mismas declaraciones de definición idénticas. Los métodos parciales se pueden sobrecargar y cada versión sobrecargada puede tener una o ninguna declaración de implementación.  
  
### Para corregir este error  
  
1.  Quite todas las declaraciones de implementación del método parcial, excepto una.  
  
## Ejemplo  
 El siguiente ejemplo genera el error CS0757:  
  
```  
// cs0757.cs using System; public partial class C { // Defining declaration. partial void Part(); // Implementing declaration. partial void Part() { //...Do something. } // Second implementing declaration. partial void Part() // CS0757 { //...Do something. } public static int Main() { return 1; } }  
```  
  
## Vea también  
 [Clases y métodos parciales](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)