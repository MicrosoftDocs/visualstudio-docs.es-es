---
title: "Soluci&#243;n de problemas de excepciones: Microsoft.Office.Tools.InvalidRangeException | Microsoft Docs"
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
  - "Microsoft.Office.Tools.InvalidRangeException (excepción)"
ms.assetid: 0deea25b-1152-40b6-89e2-e2e9c85f7dc0
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: Microsoft.Office.Tools.InvalidRangeException
Se produce una excepción <xref:Microsoft.Office.Tools.InvalidRangeException> cuando se crea mediante programación un control de vista con un intervalo que abarca varias áreas.  
  
## Sugerencias asociadas  
 Asegúrese de que el área cubierta por el intervalo no solapa a la de otro intervalo.  
 Los intervalos no se pueden superponer.  
  
 Cuando cree mediante programación un control de vista, asegúrese de que solo incluye un área única.  
 -   Cuando cree mediante programación un control de vista, asegúrese de que solo incluye un área única; o sea, todas las celdas deben estar juntas.  
  
## Vea también  
 <xref:Microsoft.Office.Tools.InvalidRangeException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)