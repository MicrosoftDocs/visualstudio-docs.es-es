---
title: "No se pueden leer los campos delimitados porque una comilla doble no es un delimitador v&#225;lido cuando EscapeQuotes se establece en True. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrTextFieldParser_IllegalDelimiter"
ms.assetid: ab8a0c3a-b89c-4617-9e31-7e81f5dca433
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se pueden leer los campos delimitados porque una comilla doble no es un delimitador v&#225;lido cuando EscapeQuotes se establece en True.
El `TextFieldParser` no se puede leer desde el archivo porque se han proporcionado comillas \("\) como delimitador y `EscapeQuotes` está establecido en `True`.  
  
### Para corregir este error  
  
-   Establezca `EscapeQuotes` en `False`.  
  
## Vea también  
 [Método TextFieldParser.SetDelimiters](http://msdn.microsoft.com/es-es/21fa40ec-5866-4d0e-9fd9-c708a190dcc9)   
 [Propiedad TextFieldParser.Delimiters](http://msdn.microsoft.com/es-es/4eb18f4d-3011-40a9-b668-be93eed0444f)   
 [Cómo: Leer archivos de texto delimitado por comas](../Topic/How%20to:%20Read%20From%20Comma-Delimited%20Text%20Files%20in%20Visual%20Basic.md)   
 [TextFieldParser \(Objeto\)](/dotnet/visual-basic/language-reference/objects/textfieldparser-object)