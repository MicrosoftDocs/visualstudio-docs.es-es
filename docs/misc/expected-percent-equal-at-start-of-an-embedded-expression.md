---
title: "Se esperaba &#39;%=&#39; al principio de una expresi&#243;n insertada | Microsoft Docs"
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
  - "vbc31179"
  - "bc31179"
helpviewer_keywords: 
  - "BC31179"
ms.assetid: 20b0382e-1744-47e4-84e1-7fc926cbc4df
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Se esperaba &#39;%=&#39; al principio de una expresi&#243;n insertada
El identificador de inicio de una expresión insertada, `<%=`, no se codificó correctamente. Tenga en cuenta que no puede usar un carácter de porcentaje \(%\) en el nombre de un literal de elemento XML.  
  
 **Identificador de error:** BC31179  
  
### Para corregir este error  
  
-   Asegúrese de que el identificador de inicio de la expresión  insertada esté codifico como `<%=`.  
  
## Vea también  
 [Expresiones incrustadas en XML](/dotnet/visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml)   
 [Literales XML](/dotnet/visual-basic/language-reference/xml-literals/index)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)