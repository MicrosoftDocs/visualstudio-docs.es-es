---
title: "Soluci&#243;n de problemas de excepciones: System.Runtime.InteropServices.SafeArrayRankMismatchException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EHSafeArrayRankMismatch"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "SafeArrayRankMismatchException (clase)"
ms.assetid: 6c69355c-8bfd-49bb-acad-b4d7236ae2e7
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.Runtime.InteropServices.SafeArrayRankMismatchException
Se produce una excepción <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException> cuando el rango de un SAFEARRAY de entrada no coincide con el rango especificado en la firma administrada.  
  
## Sugerencias asociadas  
 **Asegúrese de que su matriz tiene el número necesario de dimensiones.**  
 Como el rango y los límites de la matriz segura no pueden determinarse a partir de la biblioteca de tipos, el rango se considera igual a 1 y el límite inferior igual a 0. El rango y los límites se deben definir en la firma administrada generada por [Tlbimp.exe \(Type Library Importer\)](../Topic/Tlbimp.exe%20\(Type%20Library%20Importer\).md).  
  
## Vea también  
 <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Default Marshaling for Arrays](../Topic/Default%20Marshaling%20for%20Arrays.md)   
 [Matrices](/dotnet/visual-basic/programming-guide/language-features/arrays/index)