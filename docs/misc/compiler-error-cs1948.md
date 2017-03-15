---
title: "Error del compilador CS1948 | Microsoft Docs"
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
  - "CS1948"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1948"
ms.assetid: 3dac3abe-0edd-4ee1-8fb1-bc597ea63e1f
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1948
La variable de rango 'name' no puede tener el mismo nombre que un parámetro de tipo de método  
  
 El mismo espacio de declaración no puede contener dos declaraciones del mismo identificador.  
  
### Para corregir este error  
  
1.  Cambie el nombre de la variable de rango o el parámetro de tipo.  
  
## Ejemplo  
 El ejemplo siguiente genera CS1948 porque el identificador `T` se usa para la variable de rango y para el parámetro de tipo en el método `TestMethod`:  
  
```  
// cs1948.cs using System.Linq; class Test { public void TestMethod<T>(T t) { var x = from T in Enumerable.Range(1, 100) // CS1948 select T; } }  
```