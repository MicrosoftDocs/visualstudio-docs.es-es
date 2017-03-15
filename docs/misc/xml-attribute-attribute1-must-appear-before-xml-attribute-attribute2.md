---
title: "El atributo XML &#39;attribute1&#39; debe aparecer antes del atributo XML &#39;attribute2&#39; | Microsoft Docs"
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
  - "bc31157"
  - "vbc31157"
helpviewer_keywords: 
  - "BC31157"
ms.assetid: d8d8769e-533d-454e-b145-99955ce45cc5
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El atributo XML &#39;attribute1&#39; debe aparecer antes del atributo XML &#39;attribute2&#39;
Los atributos de un literal de documento XML se especifican en un orden no válido. El orden de atributo válido para un literal de documento XML se basa en la especificación XML 1.0. Por ejemplo, el atributo `encoding` de un literal de documento XML debe seguir inmediatamente el atributo `version`.  
  
 **Identificador de error:** BC31157  
  
### Para corregir este error  
  
-   Actualice el orden de atributo para el literal de documento XML con las directrices especificadas en la especificación XML 1.0.  
  
## Vea también  
 [Literales XML y la especificación XML 1.0](/dotnet/visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification)   
 [Literal de documento XML](/dotnet/visual-basic/language-reference/xml-literals/xml-document-literal)   
 [Literales XML](/dotnet/visual-basic/language-reference/xml-literals/index)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)