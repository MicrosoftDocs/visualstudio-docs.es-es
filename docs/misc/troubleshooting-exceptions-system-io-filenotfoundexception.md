---
title: "Soluci&#243;n de problemas de excepciones: System.IO.FileNotFoundException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
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
  - "FileNotFoundException (clase)"
  - "System.IO.FileNotFoundException (excepción)"
ms.assetid: 6e5ab395-7c81-434e-835f-0fc792b9149d
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.IO.FileNotFoundException
Si se intenta obtener acceso a un archivo o un directorio que no existe en el disco, se produce una excepción <xref:System.IO.FileNotFoundException>.  
  
## Sugerencias asociadas  
 **Compruebe que el archivo existe en la ubicación especificada.**  
 Si el archivo no existe, se desencadena esta excepción. Para obtener más información, consulta <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A>.  
  
 **Cuando utilice rutas de acceso relativas, asegúrese de que el directorio sea el correcto.**  
 Si asume de forma incorrecta el directorio actual, las rutas de acceso relativas también serán incorrectas.  
  
## Vea también  
 <xref:System.IO.FileNotFoundException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)