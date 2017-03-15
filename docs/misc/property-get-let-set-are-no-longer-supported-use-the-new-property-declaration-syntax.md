---
title: "Ya no se admiten las propiedades Get/Let/Set; utilice la nueva sintaxis de declaraci&#243;n Property | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30808"
  - "bc30808"
helpviewer_keywords: 
  - "BC30808"
ms.assetid: c8a803eb-316d-4f73-b6ef-27a2914409f3
caps.latest.revision: 10
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Ya no se admiten las propiedades Get/Let/Set; utilice la nueva sintaxis de declaraci&#243;n Property
`Property Get/Let/Set` ya no se admiten; use la nueva sintaxis de declaración `Property`.  
  
 La sintaxis para declarar propiedades ha cambiado. Ahora, las propiedades se definen dentro de los bloques.  
  
 **Id. de error:** BC30808  
  
### Para corregir este error  
  
1.  Defina propiedades en bloques de código que comiencen por la palabra clave `Property`. Propiedades End con la construcción `End Property`.  
  
2.  Defina procedimientos de la propiedad `Get` dentro de bloques de propiedades con la palabra clave `Get`. Finalice los procedimientos de la propiedad `Get` con la construcción `End Get`.  
  
3.  Defina procedimientos de la propiedad `Set` dentro de bloques de propiedades con la palabra clave `Set`. Finalice los procedimientos de la propiedad `Set` con la construcción `End Set`.  
  
4.  Use los procedimientos de la propiedad `Set` para todas las asignaciones de propiedades. Los procedimientos de la propiedad `Let` ya no son necesarios ni compatibles.  
  
## Vea también  
 [Property \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/property-statement)   
 [Language Changes in Visual Basic](http://msdn.microsoft.com/es-es/a1be4461-a0e4-4a88-a32c-dcad41ed119a)