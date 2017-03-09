---
title: "Error de MSBuild MSB3116 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.HostInBrowserNotOnlineOnly"
helpviewer_keywords: 
  - "MSB3116"
ms.assetid: bf04c587-d0e2-4d68-bbff-da9a985ea70e
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3116
**MSB3116: La aplicación está marcada para hospedarse en el explorador, pero también está marcada para su uso con y sin conexión.  Cambie la aplicación a sólo con conexión.**  
  
 Cuando implemente una aplicación de explorador web WPF, debe establecer la propiedad <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.ApplicationManifest.HostInBrowser%2A> en `True`.  Cuando la propiedad <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.ApplicationManifest.HostInBrowser%2A> está establecida en `True`, debe establecer la propiedad <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.DeployManifest.Install%2A> en `False` \(para que la instalación esté disponible sólo en línea\).  Si no se cumple esta última condición, recibirá este mensaje de error.  
  
### Para corregir este error  
  
-   Establezca la propiedad <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.DeployManifest.Install%2A> en `False`.  
  
## Vea también  
 <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.ApplicationManifest.HostInBrowser%2A>   
 <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.DeployManifest.Install%2A>   
 [Panel Publicar, Diseñador de proyectos](../ide/reference/publish-page-project-designer.md)