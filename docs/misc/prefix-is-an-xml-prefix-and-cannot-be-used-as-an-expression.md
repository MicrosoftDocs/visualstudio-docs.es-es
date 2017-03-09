---
title: "&#39;prefijo&#39; es un prefijo XML y no se puede usar como una expresi&#243;n | Microsoft Docs"
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
  - "bc30114"
  - "vbc30114"
helpviewer_keywords: 
  - "BC30114"
ms.assetid: 5cb7c89e-c61b-483a-9369-5285b7cbcf45
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;prefijo&#39; es un prefijo XML y no se puede usar como una expresi&#243;n
'prefijo' es un prefijo XML y no se puede usar como una expresión. Use el operador GetXmlNamespace para crear un objeto de espacio de nombres.  
  
 El prefijo de espacio de nombres XML que se importa mediante la instrucción `Imports` no se puede usar fuera de un literal XML.  
  
 **Identificador de error:** BC30114  
  
### Para corregir este error  
  
-   Si tiene que hacer referencia a la parte del espacio de nombres XML importado, use el operador `GetXmlNamespace` para recuperar un objeto <xref:System.Xml.Linq.XNamespace>. Use ese objeto en lugar del prefijo de espacio de nombres XML.  
  
-   Si está usando el prefijo de espacio de nombres XML para calificar un literal XML, asegúrese de que está usando la sintaxis adecuada para el literal XML.  
  
## Vea también  
 [Literales XML](/dotnet/visual-basic/language-reference/xml-literals/index)   
 [Imports \(Instrucción, Espacio de nombres XML\)](/dotnet/visual-basic/language-reference/statements/imports-statement-xml-namespace)   
 [GetXmlNamespace \(Operador\)](/dotnet/visual-basic/language-reference/operators/getxmlnamespace-operator)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)   
 [Introducción a LINQ en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)