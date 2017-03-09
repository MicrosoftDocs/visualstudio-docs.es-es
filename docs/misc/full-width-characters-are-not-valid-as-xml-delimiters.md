---
title: "No se pueden utilizar caracteres de ancho completo como delimitadores XML. | Microsoft Docs"
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
  - "vbc31197"
  - "bc31197"
helpviewer_keywords: 
  - "BC31197"
ms.assetid: f5d724f8-545b-4cf8-9606-12c63814c6e8
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se pueden utilizar caracteres de ancho completo como delimitadores XML.
Se definió un literal XML que incluye un carácter de ancho completo como un delimitador. Los caracteres de ancho completo también se conocen como caracteres anchos o multibyte.  
  
 **Identificador de error:** BC31197  
  
### Para corregir este error  
  
-   Quite el carácter de ancho completo de la definición del literal XML y reemplácelo por un carácter delimitador ANSI válido. Algunos caracteres delimitadores válidos son: `<`, `>`, `=`, `:` y `/`.  
  
## Vea también  
 [Literales XML](/dotnet/visual-basic/language-reference/xml-literals/index)   
 [Codificación de caracteres en .NET Framework](../Topic/Character%20Encoding%20in%20the%20.NET%20Framework.md)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)