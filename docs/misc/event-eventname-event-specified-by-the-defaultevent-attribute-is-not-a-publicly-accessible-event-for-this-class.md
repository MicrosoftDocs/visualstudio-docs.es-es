---
title: "El evento &#39;&lt;eventname&gt;&#39; especificado por el atributo &#39;DefaultEvent&#39; no es un evento accesible p&#250;blicamente para esta clase. | Microsoft Docs"
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
  - "vbc30770"
  - "bc30770"
helpviewer_keywords: 
  - "BC30770"
ms.assetid: 7524fba7-2a37-4bc3-b789-87d73a166575
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El evento &#39;&lt;eventname&gt;&#39; especificado por el atributo &#39;DefaultEvent&#39; no es un evento accesible p&#250;blicamente para esta clase.
El atributo <xref:System.ComponentModel.DefaultEventAttribute> debe especificar el nombre del evento accesible públicamente en la clase a la que se aplica el atributo.  
  
 **Identificador de error:** BC30770  
  
### Para corregir este error  
  
1.  Asegúrese de que la clase define un evento accesible públicamente.  
  
2.  Asegúrese de que el nombre del evento en la clase coincide con el nombre especificado por el atributo <xref:System.ComponentModel.DefaultEventAttribute>.  
  
## Vea también  
 <xref:System.ComponentModel.DefaultEventAttribute>   
 [Event \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [Class \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/class-statement)   
 [Public](/dotnet/visual-basic/language-reference/modifiers/public)