---
title: "Soluci&#243;n de problemas de excepciones: System.DeploymentFramework.DependentPlatformMissingException | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "clase DependentPlatformMissingException, solución de problemas"
ms.assetid: fee1ca1c-0f0b-483b-b8ab-3743dfdda038
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.DeploymentFramework.DependentPlatformMissingException
Se produce una excepción `T:System.DeploymentFramework.DependentPlatformMissingException` cuando una aplicación depende de algo no instalado en este cliente. Una de las posibles causas puede ser que se trate de un error del sistema operativo o de la versión de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] que hay en el equipo al que se implementa la aplicación.  
  
## Sugerencias asociadas  
 **Compruebe que todos los ensamblados requeridos por la aplicación se instalan en el equipo de destino.**  
 Cada instalación que intenta utilizar Windows Installer comienza comprobando si el instalador se encuentra presente en el equipo del usuario; si no es así, comprueba si el equipo está preparado para instalar Windows Installer.  
  
## Vea también  
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)