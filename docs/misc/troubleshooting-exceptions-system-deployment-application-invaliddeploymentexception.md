---
title: "Soluci&#243;n de problemas de excepciones: System.Deployment.Application.InvalidDeploymentException | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "InvalidDeploymentException (clase)"
ms.assetid: 4361e053-8eaf-44e3-b8ac-95516d8d1832
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.Deployment.Application.InvalidDeploymentException
Cuando la aplicación o sus manifiestos de aplicación e implementación no son válidos, se produce una excepción <xref:System.Deployment.Application.InvalidDeploymentException>.  
  
## Sugerencias asociadas  
 **Asegúrese de que son válidos los manifiestos para esta aplicación.**  
 Un manifiesto de aplicación es un archivo XML que describe e identifica los ensamblados en paralelo, compartidos y privados, a los que debe enlazarse una aplicación en tiempo de ejecución. Deben ser las mismas versiones de ensamblado utilizadas para probar la aplicación. Los manifiestos de aplicación también describen los metadatos para archivos privados de la aplicación.  
  
 **Use la característica ClickOnce para implementar la aplicación.**  
 Utilice ClickOnce para publicar aplicaciones para Windows en un servidor Web o recurso compartido de archivos de red, a fin de simplificar la instalación. Para obtener más información, consulta [Seguridad e implementación ClickOnce](../deployment/clickonce-security-and-deployment.md).  
  
## Vea también  
 <xref:System.Deployment.Application.InvalidDeploymentException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Solucionar problemas en implementaciones ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)   
 [ClickOnce Deployment for Windows Forms](../Topic/ClickOnce%20Deployment%20for%20Windows%20Forms.md)