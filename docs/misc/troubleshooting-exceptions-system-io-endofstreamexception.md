---
title: "Soluci&#243;n de problemas de excepciones: System.IO.EndOfStreamException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "EndOfStreamException (clase)"
ms.assetid: 1271e6f6-3a0d-49f0-9ff4-178d480687be
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.IO.EndOfStreamException
Si se intenta leer después del final de una secuencia, se produce una excepción <xref:System.IO.EndOfStreamException>.  
  
## Sugerencias asociadas  
 **Compruebe si se alcanzó el final del archivo antes de leerlo.**  
 Utilice el método <xref:System.IO.StreamReader.Peek%2A> para comprobar el fin del archivo antes de leer en la secuencia.  
  
## Vea también  
 <xref:System.IO.EndOfStreamException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Cómo: Leer y escribir en un archivo de datos recién creado](../Topic/How%20to:%20Read%20and%20Write%20to%20a%20Newly%20Created%20Data%20File.md)   
 [Cómo: Abrir y anexar a un archivo de registro](../Topic/How%20to:%20Open%20and%20Append%20to%20a%20Log%20File.md)