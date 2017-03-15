---
title: "Error de an&#225;lisis de documentaci&#243;n XML: la etiqueta inicial &#39;&lt;etiqueta&gt;&#39; no tiene la correspondiente etiqueta de cierre. | Microsoft Docs"
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
  - "vbc42316"
  - "BC42316"
helpviewer_keywords: 
  - "BC42316"
ms.assetid: 45b68176-ebf6-43af-820e-6801aabb6c57
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Error de an&#225;lisis de documentaci&#243;n XML: la etiqueta inicial &#39;&lt;etiqueta&gt;&#39; no tiene la correspondiente etiqueta de cierre.
Error de análisis de documentación XML: la etiqueta inicial \<etiqueta\> no tiene la correspondiente etiqueta de cierre. Se omitirá el comentario XML.  
  
 El comentario XML contiene una etiqueta inicial pero no contiene una etiqueta final correspondiente.  
  
 **Identificador de error:** BC42316  
  
### Para corregir este error  
  
-   Agregue una etiqueta final que corresponda a la etiqueta inicial.  
  
     o  
  
-   Si la etiqueta no contiene texto interno, como [\<seealso\>](../Topic/%3Cseealso%3E%20\(Visual%20Basic\).md), especifique una barra diagonal antes del corchete angular de cierre.  
  
## Vea también  
 [Etiquetas XML para comentarios](/dotnet/visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments)   
 [Documentar el código con XML](/dotnet/visual-basic/programming-guide/program-structure/documenting-your-code-with-xml)