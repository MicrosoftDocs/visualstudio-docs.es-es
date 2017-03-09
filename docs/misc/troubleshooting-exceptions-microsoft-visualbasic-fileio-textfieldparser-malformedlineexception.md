---
title: "Soluci&#243;n de problemas de excepciones: Microsoft.VisualBasic.FileIO.TextFieldParser.MalformedLineException | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Microsoft.VisualStudio.Tools.Applications.Runtime.ControlNotFoundException (excepción)"
ms.assetid: d780b8cc-c3f1-45ed-8f8e-3f8728a4b770
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: Microsoft.VisualBasic.FileIO.TextFieldParser.MalformedLineException
Se produce una excepción <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> cuando un <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> no puede analizar una fila utilizando el formato especificado.  
  
 La propiedad `Error Line` del objeto de excepción contiene el texto de la línea que produce el error.  
  
## Sugerencias asociadas  
 **Compruebe que los parámetros TextFieldType y Delimiter están correctamente definidos**  
 El tipo `TextFieldType` \(delimitado o de ancho fijo\) debe coincidir con el formato del archivo. Si la palabra clave `TextFieldType` es `FixedWidth`, compruebe que se ha establecido correctamente la propiedad `FieldWidths`. Si la palabra clave `TextFieldType` es `Delimited`, compruebe que se ha establecido correctamente la propiedad `Delimiters`.  
  
## Vea también  
 <xref:Microsoft.VisualBasic.FileIO.MalformedLineException>   
 [Analizar archivos de texto con el objeto TextFieldParser](/dotnet/visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object)   
 [Cómo: Leer archivos de texto delimitado por comas](../Topic/How%20to:%20Read%20From%20Comma-Delimited%20Text%20Files%20in%20Visual%20Basic.md)   
 [Cómo: Leer archivos de texto de ancho fijo](../Topic/How%20to:%20Read%20From%20Fixed-width%20Text%20Files%20in%20Visual%20Basic.md)