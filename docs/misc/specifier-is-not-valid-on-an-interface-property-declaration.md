---
title: "&#39;&lt;especificador&gt;&#39; no es v&#225;lido en una declaraci&#243;n de propiedad de interfaz | Microsoft Docs"
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
  - "vbc30273"
  - "bc30273"
helpviewer_keywords: 
  - "BC30273"
ms.assetid: f10c4f5f-6176-4dba-99a9-b58f3b390fba
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;especificador&gt;&#39; no es v&#225;lido en una declaraci&#243;n de propiedad de interfaz
Una instrucción `Property` dentro de una interfaz contiene una palabra clave no válida, como `Implements`. Una interfaz solo puede definir los miembros, no implementarlos.  
  
 **Identificador de error:** BC30273  
  
### Para corregir este error  
  
-   Quite la palabra clave no válida de la instrucción de declaración.  
  
-   Mueva la implementación de los miembros de interfaz a una clase que implemente la interfaz.  
  
## Vea también  
 [Interface \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/interface-statement)   
 [Implements \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/implements-statement)