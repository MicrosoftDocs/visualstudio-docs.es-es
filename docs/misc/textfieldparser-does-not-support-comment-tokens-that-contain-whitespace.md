---
title: "TextFieldParser no admite tokens de comentarios que contengan espacios en blanco. | Microsoft Docs"
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
  - "vbrTextFieldParser_WhitespaceInToken"
ms.assetid: 55107656-270e-4bbb-841a-478904df8e07
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# TextFieldParser no admite tokens de comentarios que contengan espacios en blanco.
Se ha proporcionado un token de comentario que contiene espacios en blanco. El `TextFieldParser` no admite tokens de comentarios que contengan espacios en blanco a menos que el espacio en blanco aparezca al principio del token. Se omite el espacio en blanco que aparece al principio de un token.  
  
### Para corregir este error  
  
-   Proporcione un token de comentario correcto.  
  
## Vea también  
 [Propiedad TextFieldParser.CommentTokens](http://msdn.microsoft.com/es-es/2e6b6435-4bee-4c14-a353-e8f2c82e2d61)   
 [Analizar archivos de texto con el objeto TextFieldParser](/dotnet/visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object)   
 [TextFieldParser \(Objeto\)](/dotnet/visual-basic/language-reference/objects/textfieldparser-object)