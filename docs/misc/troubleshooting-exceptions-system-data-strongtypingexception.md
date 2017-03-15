---
title: "Soluci&#243;n de problemas de excepciones: System.Data.StrongTypingException | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "StrongTypingException (clase)"
ms.assetid: 90859ce2-3696-43cb-baf4-7daf98d8e2e1
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.Data.StrongTypingException
<xref:System.Data.StrongTypingException> se produce cuando el usuario tiene acceso a un valor <xref:System.DBNull> en un <xref:System.Data.DataTable.DataSet%2A> fuertemente tipado.  
  
## Sugerencias asociadas  
 **Agregue el control de errores para StrongTypingException.**  
 Coloque el código que tiene acceso a <xref:System.Data.DataTable.DataSet%2A> en un bloque `Try…Catch` y detecte <xref:System.Data.StrongTypingException>.  
  
## Vea también  
 <xref:System.Data.DataTable.DataSet%2A>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Try...Catch...Finally \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Trabajar con los conjuntos de datos en Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)