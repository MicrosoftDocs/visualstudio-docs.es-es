---
title: "Soluci&#243;n de problemas de excepciones: System.Deployment.DependentPlatformMissingException | Microsoft Docs"
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
  - "DependentPlatformMissingException (clase)"
ms.assetid: 2343eb4f-f23f-4b6c-a65c-1f93c3e6ea36
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.Deployment.DependentPlatformMissingException
Si se intenta ejecutar una aplicación en un equipo que no es compatible, se produce una excepción `T:System.Deployment.DependentPlatformMissingException`. Esto puede suceder si se instala el sistema operativo o la versión de .NET Framework incorrectos en el equipo de destino.  
  
## Sugerencias asociadas  
 **Asegúrese de que todos los ensamblados necesarios para la aplicación están instalados en el equipo de destino.**  
 Cada instalación que intenta utilizar Windows Installer comienza comprobando si el instalador se encuentra presente en el equipo del usuario; si no es así, comprueba si el equipo está preparado para instalar Windows Installer.  
  
## Vea también  
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)