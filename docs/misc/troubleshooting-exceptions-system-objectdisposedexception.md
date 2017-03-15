---
title: "Soluci&#243;n de problemas de excepciones: System.ObjectDisposedException | Microsoft Docs"
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
  - "Clase ObjectDisposedException, solución de problemas"
ms.assetid: 702912b6-e927-4f8e-8b7c-2e1880312b0e
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.ObjectDisposedException
Cuando se intenta realizar una operación en un objeto desechado, como una secuencia cerrada o una clave del Registro, se produce una excepción <xref:System.ObjectDisposedException>.  
  
## Sugerencias asociadas  
 **Asegúrese de que no ha liberado un recurso antes de intentar utilizarlo.**  
 Por ejemplo, si intenta manipular una secuencia, asegúrese de que no se ha cerrado previamente.  
  
## Vea también  
 <xref:System.ObjectDisposedException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)