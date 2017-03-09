---
title: "Soluci&#243;n de problemas de excepciones: System.MissingMethodException | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
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
  - "MissingMethodException (clase)"
ms.assetid: 1ca4c351-ca26-4a6d-a5a1-c484ac193e2e
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.MissingMethodException
Si se intenta tener acceso de forma dinámica a un método que no existe, se produce una excepción <xref:System.MissingMethodException>.  
  
## Sugerencias asociadas  
 **Si se ha quitado o cambiado el nombre de un método en una biblioteca de clases, vuelva a compilar los ensamblados que hagan referencia a dicho método.**  
 Generalmente, esta excepción se produce cuando se intenta tener acceso de forma dinámica a un método eliminado o cuyo nombre ha cambiado en un ensamblado al que no se hace referencia por su nombre seguro.  
  
## Comentarios  
 Si llama a una función no administrada, se produce esta excepción si CLR no puede encontrar el módulo o la función.  
  
## Vea también  
 <xref:System.MissingMethodException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Solución de problemas de interoperabilidad](/dotnet/visual-basic/programming-guide/com-interop/troubleshooting-interoperability)