---
title: "Soluci&#243;n de problemas de excepciones: System.FieldAccessException | Microsoft Docs"
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
  - "FieldAccessException (clase)"
ms.assetid: 47a72daf-500e-494c-b2fe-374edad2e9cd
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.FieldAccessException
Si se produce un intento no válido de obtener acceso a un campo privado o protegido dentro de una clase, se produce una excepción <xref:System.FieldAccessException>.  
  
## Sugerencias asociadas  
 **Si el nivel de acceso de un campo en una biblioteca de clase ha cambiado, vuelva a compilar los ensamblados que hagan referencia a esta biblioteca.**  
 Generalmente, esta excepción se produce cuando cambia el nivel de acceso \(`Public`, `Private`, etc.\) de un campo en una biblioteca de clases y no se han vuelto a compilar uno o varios ensamblados que hacen referencia a la biblioteca.  
  
## Vea también  
 <xref:System.FieldAccessException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)