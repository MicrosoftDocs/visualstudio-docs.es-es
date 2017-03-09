---
title: "Soluci&#243;n de problemas de excepciones: System.IO.IOException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IOException (clase)"
ms.assetid: 87812daa-0784-43dc-b3dc-6652a960c362
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.IO.IOException
Cuando se produce un error de E\/S, como un error de lectura o escritura en un archivo, se produce <xref:System.IO.IOException>.  
  
## Sugerencias asociadas  
 **Asegúrese de que el archivo y el directorio existen.**  
 Compruebe que el directorio en el que intenta leer o escribir existe. Compruebe que el archivo que intenta leer existe.  
  
### Comentarios  
 <xref:System.IO.IOException> es la clase base para excepciones que se producen mientras se tiene acceso a la información mediante secuencias, archivos y directorios.  
  
 La biblioteca de clases base incluye los siguientes tipos, cada uno de los cuales son una clase derivada de <xref:System.IO.IOException>:  
  
-   <xref:System.IO.DirectoryNotFoundException>  
  
-   <xref:System.IO.EndOfStreamException>  
  
-   <xref:System.IO.FileNotFoundException>  
  
-   <xref:System.IO.FileLoadException>  
  
-   <xref:System.IO.PathTooLongException>  
  
## Vea también  
 <xref:System.IO.IOException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [NOTINBUILD Cómo: crear aplicaciones de consola CLR](http://msdn.microsoft.com/es-es/b8af4197-e65f-4b17-b18e-b9e92965d026)