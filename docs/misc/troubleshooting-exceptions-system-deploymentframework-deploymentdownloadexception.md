---
title: "Soluci&#243;n de problemas de excepciones: System.DeploymentFramework.DeploymentDownloadException | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "DeploymentDownloadException (clase)"
  - "implementación de aplicaciones [C#], clase DeploymentDownloadException"
  - "implementar aplicaciones [C#], clase DeploymentDownloadException"
ms.assetid: 55ec7af5-b1d1-4db2-8af8-3c708f521cc7
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.DeploymentFramework.DeploymentDownloadException
Si se produce una excepción de red de cualquier tipo cuando se descarga una actualización de aplicación, se produce `T:System.DeploymentFramework.DeploymentDownloadException`.  
  
## Sugerencias asociadas  
 **Examine InnerException para determinar el System.Net subyacente o la excepción System.IO.**  
 Esta excepción se produce siempre que hay una excepción de red al descargar una actualización de la aplicación. Examine la propiedad <xref:System.Exception.InnerException%2A> de la excepción para determinar la excepción subyacente.  
  
## Vea también  
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Try...Catch...Finally \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)