---
title: "El comentario XML tiene una etiqueta con un atributo &#39;cref&#39; &#39;&lt;attribute&gt;&#39; que no se pudo resolver | Microsoft Docs"
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
  - "bc42309"
  - "vbc42309"
helpviewer_keywords: 
  - "BC42309"
ms.assetid: c9f3cfa5-565f-48bf-8616-cfb25d24f89e
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El comentario XML tiene una etiqueta con un atributo &#39;cref&#39; &#39;&lt;attribute&gt;&#39; que no se pudo resolver
El comentario XML tiene una etiqueta con un atributo 'cref' '\<attribute\>' que no se pudo resolver. Se omitirá el comentario XML.  
  
 Las etiquetas pueden tener un atributo `cref` que designe un vínculo a otro elemento del código XML mediante la especificación del nombre relativo del identificador. En tiempo de compilación, el compilador reemplaza el valor por el identificador XML calificado del valor al que apunta el usuario. El compilador utiliza sus reglas de resolución normales para localizar el tipo o el miembro.  
  
 **Id. de error:** BC42309  
  
### Para corregir este error  
  
-   Valide el atributo `cref` para que apunte a un elemento de código válido.  
  
## Vea también  
 [Cómo: Crear documentación XML](../Topic/How%20to:%20Create%20XML%20Documentation%20in%20Visual%20Basic.md)   
 [Etiquetas XML para comentarios](/dotnet/visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments)