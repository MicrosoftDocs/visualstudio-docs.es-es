---
title: "El comentario XML no se puede aplicar m&#225;s de una vez en un &lt;tipo&gt; parcial. | Microsoft Docs"
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
  - "bc42314"
  - "vbc42314"
helpviewer_keywords: 
  - "BC42314"
ms.assetid: 23c76238-843a-44fe-88b7-25e604ee924b
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El comentario XML no se puede aplicar m&#225;s de una vez en un &lt;tipo&gt; parcial.
El comentario XML no se puede aplicar más de una vez en un \<tipo\> parcial. Se omitirán los comentarios XML para este \<tipo\>.  
  
 Un bloque de comentario XML puede aparecer solo sobre una parte de un tipo parcial.  
  
 Si un bloque de comentario XML aparece sobre más de una parte de un tipo parcial, esta advertencia se crea para cada bloque de comentario y se omite el comentario XML de nivel superior.  
  
 **Identificador de error:** BC42314  
  
### Para corregir este error  
  
-   Elimine los bloques con comentario superfluos.  
  
## Vea también  
 [Cómo: Crear documentación XML](../Topic/How%20to:%20Create%20XML%20Documentation%20in%20Visual%20Basic.md)   
 [Etiquetas XML para comentarios](/dotnet/visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments)