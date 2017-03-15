---
title: "&#39;&lt;especificador&gt;&#39; no es v&#225;lido en una declaraci&#243;n de m&#233;todo de interfaz | Microsoft Docs"
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
  - "bc30270"
  - "vbc30270"
helpviewer_keywords: 
  - "BC30270"
ms.assetid: 598f2944-3e5d-4686-b6f7-2b4bcaf5c211
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;especificador&gt;&#39; no es v&#225;lido en una declaraci&#243;n de m&#233;todo de interfaz
Una instrucción `Function` o `Sub` dentro de una interfaz contiene una palabra clave no válida, como `Implements`. Una interfaz solo puede definir los miembros, no implementarlos.  
  
 **Identificador de error:** BC30270  
  
### Para corregir este error  
  
1.  Quite la palabra clave no válida de la instrucción de declaración.  
  
2.  Mueva la implementación de los miembros de interfaz a una clase que implemente la interfaz.  
  
## Vea también  
 [Interface \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/interface-statement)   
 [Implements \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/implements-statement)