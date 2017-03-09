---
title: "&#39;&lt;especificador&gt;&#39; no es v&#225;lido en una declaraci&#243;n de evento de interfaz | Microsoft Docs"
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
  - "bc30275"
  - "vbc30275"
helpviewer_keywords: 
  - "BC30275"
ms.assetid: bd12c952-c619-4753-8d6d-90ef4086fdc2
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;especificador&gt;&#39; no es v&#225;lido en una declaraci&#243;n de evento de interfaz
Una instrucción `Event` dentro de una interfaz contiene una palabra clave que no está permitida, como `Implements`. Una interfaz solo puede definir los miembros, no implementarlos.  
  
 **Identificador de error:** BC30275  
  
### Para corregir este error  
  
1.  Quite la palabra clave de la instrucción de declaración.  
  
2.  Mueva la implementación de los miembros de interfaz a una clase que implemente la interfaz.  
  
## Vea también  
 [Interface \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/interface-statement)   
 [Implements \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/implements-statement)