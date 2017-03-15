---
title: "Soluci&#243;n de problemas de excepciones: System.Data.ReadOnlyException | Microsoft Docs"
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
  - "ReadOnlyException (clase)"
ms.assetid: 1ac5da38-c5af-4fec-8fe1-1b9dd5069e59
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.Data.ReadOnlyException
Se produce una excepción <xref:System.Data.ReadOnlyException> cuando hay un intento para cambiar el valor de una columna de datos de sólo lectura.  
  
## Sugerencias asociadas  
 **Cambie la columna a lectura o escritura.**  
 Se produce esta excepción si está intentando cambiar un valor en una columna de datos que es de sólo lectura. Para obtener más información, consulta <xref:System.Data.DataColumn>.  
  
 **Asegúrese de que está modificando los datos en la columna correcta.**  
 Se produce esta excepción si está intentando cambiar un valor en una columna de datos que es de sólo lectura. Para obtener más información, consulta <xref:System.Data.DataColumn>.  
  
## Vea también  
 <xref:System.Data.ReadOnlyException>   
 <xref:System.Data.DataRow.EndEdit%2A>   
 <xref:System.Data.DataRow.ItemArray%2A>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)