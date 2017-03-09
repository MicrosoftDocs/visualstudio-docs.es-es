---
title: "Soluci&#243;n de problemas de excepciones: System.AccessViolationException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "System.AccessViolationException (excepción)"
  - "AccessViolationException (clase)"
ms.assetid: 7f09315d-8aad-4ab1-8b5e-21a8c97f6c14
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.AccessViolationException
Cuando se intenta leer o escribir en la memoria protegida, se produce una excepción <xref:System.AccessViolationException>.  
  
## Sugerencias asociadas  
 Asegúrese de que la memoria a la que intenta obtener acceso se haya asignado.  
 La administración automática de la memoria es uno de los servicios que proporciona Common Language Runtime. Es posible que desee desplazarse al código administrado para aprovechar este servicio. Para obtener más información, consulta [Administración de memoria automática](../Topic/Automatic%20Memory%20Management.md).  
  
 Asegúrese de que la memoria a la que intenta obtener acceso no esté dañada.  
 Si se han realizado varias operaciones de lectura o escritura con punteros no válidos, es posible que la memoria esté dañada.  
  
### Comentarios  
 Se produce una infracción de acceso en código no administrado o no seguro cuando éste intenta leer o escribir en memoria que no se ha asignado o a la que no tiene acceso. No todas las lecturas o escrituras con punteros no válidos llevan a infracciones de acceso; por lo tanto, una infracción de acceso suele indicar que se han realizado varias lecturas o escrituras con punteros no válidos y se ha dañado la memoria.  
  
 En código administrado, todas las referencias son válidas o nulas. Toda operación que intenta hacer referencia a una referencia nula en código comprobable produce una excepción <xref:System.NullReferenceException>.  
  
 Cuando se produce una infracción de acceso en código administrado no seguro, se expresa como una excepción <xref:System.NullReferenceException> o <xref:System.AccessViolationException>, dependiendo de la plataforma.  
  
 Las infracciones de acceso en código no administrado que ascienden a código administrado siempre se ajustan a una excepción <xref:System.AccessViolationException>.  
  
## Vea también  
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Administración de memoria: Ejemplos](../Topic/Memory%20Management:%20Examples.md)   
 [Administración de memoria automática](../Topic/Automatic%20Memory%20Management.md)