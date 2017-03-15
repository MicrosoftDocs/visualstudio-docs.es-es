---
title: "Error de MSBuild MSB3117 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateManifest.HostInBrowserInvalidFrameworkVersion"
helpviewer_keywords: 
  - "MSB3117"
ms.assetid: 18aec642-6000-4626-bf75-f3547769c780
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3117
**MSB3117: La aplicación se ha definido para hospedarse en el explorador, pero TargetFrameworkVersion está establecido en v2.0.**  
  
 Se implementó una aplicación de explorador web WPF con la propiedad <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.ApplicationManifest.HostInBrowser%2A> establecida en `True`, pero TargetFrameworkVersion se estableció en `v2.0` o en `v3.0`.  Si utiliza este valor, también debe establecer la propiedad <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.TargetFrameworkVersion%2A> en un valor `v3.5` o posterior.  
  
### Para corregir este error  
  
-   Establezca la propiedad <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.TargetFrameworkVersion%2A> en un valor `v3.5` o posterior.  
  
## Vea también  
 <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.ApplicationManifest.HostInBrowser%2A>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.TargetFrameworkVersion%2A>   
 [Panel Publicar, Diseñador de proyectos](../ide/reference/publish-page-project-designer.md)   
 [Error de MSBuild MSB3116](../misc/msbuild-error-msb3116.md)   
 [Error de MSBuild MSB3118](../misc/msbuild-error-msb3118.md)   
 [Error de MSBuild MSB3174](../misc/msbuild-error-msb3174.md)   
 [Error de MSBuild MSB3185](../misc/msbuild-error-msb3185.md)