---
title: "Soluci&#243;n de problemas de excepciones: System.MethodAccessException | Microsoft Docs"
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
  - "MethodAccessException (clase)"
ms.assetid: 1c276666-e451-489e-8b95-25d737787030
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.MethodAccessException
Si se produce un intento no válido de obtener acceso a un método privado o protegido dentro de una clase, se produce una excepción <xref:System.MethodAccessException>.  
  
## Sugerencias asociadas  
 **Si el nivel de acceso de un método en una biblioteca de clases ha cambiado, vuelva a compilar los ensamblados que hagan referencia a dicha biblioteca.**  
 Esta excepción se produce normalmente cuando el llamador no tiene el permiso de acceso al miembro.  
  
## Vea también  
 <xref:System.MethodAccessException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)