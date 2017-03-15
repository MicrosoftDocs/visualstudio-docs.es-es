---
title: "Error de MSBuild MSB3118 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.UseApplicationTrustInvalidFrameworkVersion"
helpviewer_keywords: 
  - "MSB3118"
ms.assetid: 9bf5b430-0cfb-4da5-a7f7-04d69f20cce1
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3118
**MSB3118: La aplicación está definida para usar confianza de la aplicación, pero TargetFrameworkVersion no es v3.5.**  
  
 Este error se produce cuando se establece la propiedad <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.UseApplicationTrust%2A> en `True` y la propiedad <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.TargetFrameworkVersion%2A> en una versión inferior a `v3.5` \(por ejemplo, `v2.0`\).  
  
### Para corregir este error  
  
-   Establezca la propiedad <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.TargetFrameworkVersion%2A> en `v3.5` o superior.  
  
## Vea también  
 <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.ApplicationManifest.UseApplicationTrust%2A>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.UseApplicationTrust%2A>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.TargetFrameworkVersion%2A>   
 <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.ApplicationManifest.HostInBrowser%2A>   
 [Panel Publicar, Diseñador de proyectos](../ide/reference/publish-page-project-designer.md)   
 [Error de MSBuild MSB3116](../misc/msbuild-error-msb3116.md)   
 [Error de MSBuild MSB3117](../misc/msbuild-error-msb3117.md)   
 [Error de MSBuild MSB3119](../misc/msbuild-error-msb3119.md)   
 [Error de MSBuild MSB3174](../misc/msbuild-error-msb3174.md)   
 [Error de MSBuild MSB3185](../misc/msbuild-error-msb3185.md)