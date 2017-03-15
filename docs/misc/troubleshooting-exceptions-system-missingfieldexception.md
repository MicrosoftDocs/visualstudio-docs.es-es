---
title: "Soluci&#243;n de problemas de excepciones: System.MissingFieldException | Microsoft Docs"
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
  - "MissingFieldException (clase)"
ms.assetid: afa4d669-7d08-4b14-8341-36717a5054d6
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.MissingFieldException
Si se intenta tener acceso de forma dinámica a un campo que no existe, se produce una excepción <xref:System.MissingFieldException>.  
  
## Sugerencias asociadas  
 **Si se ha quitado o cambiado el nombre de un campo en una biblioteca de clases, vuelva a compilar los ensamblados que hagan referencia a dicha biblioteca.**  
 Esta excepción se genera cuando se intenta tener acceso de forma dinámica a un campo eliminado o cuyo nombre ha cambiado en un ensamblado al que no se hace referencia por su nombre seguro.  
  
## Vea también  
 <xref:System.MissingFieldException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)