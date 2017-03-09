---
title: "Error de MSBuild MSB3185 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.NoEntryPoint"
helpviewer_keywords: 
  - "MSB3185"
ms.assetid: 032c63c5-d662-42ba-84e1-e3ccca8cee05
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3185
**MSB3185: No se especificó EntryPoint para el manifiesto.**  
  
 Este error se genera cuando un manifiesto no especifica un punto de entrada.  Este error puede aplicarse tanto al manifiesto de aplicación como al manifiesto de implementación.  
  
### Para corregir este error  
  
-   Si utiliza la tarea GenerateApplicationManifest, asegúrese de especificar un punto de entrada válido o de establecer la propiedad TargetFrameworkVersion en "v3.5" o una versión posterior.  En el caso de un manifiesto de aplicación, un punto de entrada válido es un archivo .exe.  
  
-   Si utiliza la tarea GenerateDeploymentManifest, asegúrese de especificar puntos de entrada válidos en sus manifiestos.  En el caso de un manifiesto de implementación, un punto de entrada válido es un manifiesto de aplicación.  
  
## Vea también  
 <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.ApplicationManifest.HostInBrowser%2A>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.TargetFrameworkVersion%2A>   
 [Panel Publicar, Diseñador de proyectos](../ide/reference/publish-page-project-designer.md)   
 [\<PackageFiles\> \(Elemento\)](../deployment/packagefiles-element-bootstrapper.md)   
 [Error de MSBuild MSB3116](../misc/msbuild-error-msb3116.md)   
 [Error de MSBuild MSB3117](../misc/msbuild-error-msb3117.md)   
 [Error de MSBuild MSB3118](../misc/msbuild-error-msb3118.md)   
 [Error de MSBuild MSB3174](../misc/msbuild-error-msb3174.md)