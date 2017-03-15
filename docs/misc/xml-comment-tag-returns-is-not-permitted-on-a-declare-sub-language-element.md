---
title: "No se permite la etiqueta de comentario XML &#39;returns&#39; en un elemento de lenguaje &#39;declare sub&#39; | Microsoft Docs"
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
  - "bc42315"
  - "vbc42315"
helpviewer_keywords: 
  - "BC42315"
ms.assetid: 55ba3e8a-ba7f-42e3-a4a7-b22844e72564
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se permite la etiqueta de comentario XML &#39;returns&#39; en un elemento de lenguaje &#39;declare sub&#39;
La etiqueta de comentario XML 'returns' no se admite en un elemento de lenguaje 'declare sub'. Se omitirá el comentario XML.  
  
 Un comentario XML para una declaración `Declare Sub` no puede contener una etiqueta `<`returns`>`.  
  
 **Identificador de error:** BC42315  
  
### Para corregir este error  
  
-   Quite las etiquetas `<`returns`>` no admitidas.  
  
## Vea también  
 [\<returns\>](../Topic/%3Creturns%3E%20\(Visual%20Basic\).md)   
 [Etiquetas XML para comentarios](/dotnet/visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments)   
 [Documentar el código con XML](/dotnet/visual-basic/programming-guide/program-structure/documenting-your-code-with-xml)   
 [Declare \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/declare-statement)