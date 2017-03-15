---
title: "Soluci&#243;n de problemas de excepciones: Microsoft.VisualBasic.ApplicationServices.CantStartSingleInstanceException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CantStartSingleInstanceException (excepción)"
  - "Microsoft.VisualBasic.ApplicationServices.CantStartSingleInstanceException (excepción)"
ms.assetid: 3639f15d-9547-43da-8145-60da34782991
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: Microsoft.VisualBasic.ApplicationServices.CantStartSingleInstanceException
La excepción que se produce cuando la segunda instancia de una aplicación de instancia única no pudo conectarse con la instancia original.  
  
## Comentarios  
 Las posibles causas de este problema son:  
  
-   La instancia original ha dejado de responder.  
  
-   La aplicación no tiene permisos para crear los objetos de kernel.  
  
     El nombre base de los objetos de kernel procede de concatenar el GUID del ensamblado, el número de la versión principal y el número de la versión secundaria. Por ejemplo, el nombre base podría ser 3639f15d\-9547\-43da\-8145\-60da347829915.1.  
  
## Vea también  
 <xref:Microsoft.VisualBasic.ApplicationServices.CantStartSingleInstanceException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)