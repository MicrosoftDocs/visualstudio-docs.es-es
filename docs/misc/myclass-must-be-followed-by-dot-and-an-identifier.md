---
title: "&#39;MyClass&#39; debe ir seguido por &#39;.&#39; y un identificador | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32028"
  - "vbc32028"
helpviewer_keywords: 
  - "BC32028"
ms.assetid: a7e92b54-32b8-4072-9576-632942f05e0f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;MyClass&#39; debe ir seguido por &#39;.&#39; y un identificador
`MyClass` no es una variable de objeto verdadera y no puede aparecer por sí sola. Se usa solo para tener acceso a un miembro de la instancia actual como si fuese `NotOverridable` en la clase base.  
  
 **Identificador de error:** BC32028  
  
### Para corregir este error  
  
1.  Si piensa tener acceso a un miembro de clase, especifique el operador de acceso de miembro \(`.`\) y un miembro de la instancia actual después de `MyClass`.  
  
2.  Si no desea tener acceso a un miembro de clase, use la palabra clave `Me`.  
  
## Vea también  
 [MyClass: eliminar](http://msdn.microsoft.com/es-es/5db36f9b-f796-4b6a-ba34-cac1fde6eb62)   
 [Me](http://msdn.microsoft.com/es-es/a65973c7-cf06-4547-9b25-9fba885525c2)   
 [NotOverridable](/dotnet/visual-basic/language-reference/modifiers/notoverridable)   
 [Fundamentos de la herencia](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)