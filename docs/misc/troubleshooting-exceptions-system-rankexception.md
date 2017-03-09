---
title: "Soluci&#243;n de problemas de excepciones: System.RankException | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
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
  - "RankException (clase)"
ms.assetid: ad7aa34a-f84b-4650-aaec-a75a8b85c50f
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.RankException
Se produce una excepción <xref:System.RankException> cuando una matriz con el número equivocado de dimensiones se pasa a un método.  
  
## Sugerencias asociadas  
 **Asegúrese de que su matriz tiene el número necesario de dimensiones.**  
 Para obtener más información, los usuarios de Visual Basic pueden ver [Dimensiones de matrices en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/arrays/array-dimensions).  
  
 Para obtener más información, los usuarios de C\# pueden ver [Matrices](/dotnet/csharp/programming-guide/arrays/index).  
  
## Comentarios  
 Puesto que los subíndices de matriz empiezan en 0, el menor índice disponible para cada dimensión es siempre 0.  
  
## Vea también  
 <xref:System.RankException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Matrices](/dotnet/visual-basic/programming-guide/language-features/arrays/index)