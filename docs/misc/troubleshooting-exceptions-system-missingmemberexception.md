---
title: "Soluci&#243;n de problemas de excepciones: System.MissingMemberException | Microsoft Docs"
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
  - "MissingMemberException (clase)"
ms.assetid: c4cf497b-0554-47fe-b2e9-81ee3eb9ec04
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.MissingMemberException
Cuando intenta tener acceso en forma dinámica a un miembro de clase inexistente, se produce una excepción <xref:System.MissingMemberException>.  
  
## Sugerencias asociadas  
 **Si quitó o cambió de nombre un miembro de una biblioteca de clases, vuelva a compilar los ensamblados que hagan referencia a esa biblioteca.**  
 Esta excepción suele producirse cuando se elimina un campo o un método o se cambia su nombre en un ensamblado, y el cambio no se refleja en un segundo ensamblado que intenta tener acceso al miembro que falta.  
  
 **Si está intentando obtener acceso a miembros en una variable de objeto enlazada en tiempo de ejecución, asegúrese de que se declaró como Public.**  
 Las variables `Protected`, `Friend` y `Private` no pueden ser enlazadas en tiempo de ejecución en Visual Basic.  
  
## Vea también  
 <xref:System.MissingMemberException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)