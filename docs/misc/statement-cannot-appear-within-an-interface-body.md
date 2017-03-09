---
title: "La instrucci&#243;n no puede aparecer dentro del cuerpo de una interfaz | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30603"
  - "BC30603"
helpviewer_keywords: 
  - "BC30603"
ms.assetid: 3aef29d6-eadf-4f1f-b214-dfeae5e51c4f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La instrucci&#243;n no puede aparecer dentro del cuerpo de una interfaz
La declaración de un miembro de interfaz incluye una instrucción que finaliza el miembro del formulario `End` *membername*.  
  
 Una interfaz define solo la firma de sus miembros. Por lo tanto, los procedimientos y propiedades definidos en una interfaz solo tienen su línea inicial, que especifica el nombre y la firma. No incluya ningún código, declaración interna o instrucción `End Function`, `End Property` o `End Sub` dentro de la interfaz.  
  
 **Identificador de error:** BC30603  
  
### Para corregir este error  
  
-   quite la instrucción `End` *membername* de la definición de interfaz.  
  
## Vea también  
 [Interface \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/interface-statement)   
 [End \<palabra clave\> \(Instrucción\)](../Topic/End%20%3Ckeyword%3E%20Statement%20\(Visual%20Basic\).md)