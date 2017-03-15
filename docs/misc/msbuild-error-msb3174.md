---
title: "Error de MSBuild MSB3174 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.InvalidValue"
helpviewer_keywords: 
  - "MSB3174"
ms.assetid: 6f9a040c-7f21-40fd-bf74-03f99f265e79
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3174
**MSB3174: Valor no válido para '\<archivo\>'.**  
  
 Este error se genera cuando el proceso de compilación encuentra un problema general al comprobar el formato de un archivo de manifiesto.  El mensaje de error hace referencia al nombre de archivo del manifiesto.  
  
 Si se establece incorrectamente alguno de los parámetros siguientes, se genera este mensaje de error.  Cada uno de los parámetros enumerados es un <xref:Microsoft.Build.Tasks.GenerateApplicationManifest> o una propiedad de <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest> como <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.TargetFrameworkVersion%2A> o <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest.MinimumRequiredVersion%2A>.  
  
 Cuando la tarea es <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>, se aplican los requisitos siguientes:  
  
|Parámetro|Requisitos|  
|---------------|----------------|  
|<xref:Microsoft.Build.Tasks.GenerateManifestBase.AssemblyName%2A>|Debe ser un nombre de archivo válido.|  
|<xref:Microsoft.Build.Tasks.GenerateManifestBase.AssemblyVersion%2A>|Tiene los mismos requisitos que <xref:System.Version.%23ctor%2A>.  Todos los octetos deben ser mayores que 0.  Debe especificar los cuatro octetos.  Se aceptan cadenas vacías.|  
|<xref:Microsoft.Build.Tasks.GenerateApplicationManifest.ClrVersion%2A>|Tiene los mismos requisitos que <xref:System.Version.%23ctor%2A>.  Todos los octetos deben ser mayores que 0.  Debe especificar los cuatro octetos.  Se aceptan cadenas vacías.|  
|<xref:Microsoft.Build.Tasks.GenerateApplicationManifest.OSVersion%2A>|Tiene los mismos requisitos que <xref:System.Version.%23ctor%2A>.  Todos los octetos deben ser mayores que 0.  Debe especificar los cuatro octetos.  Se aceptan cadenas vacías.|  
|<xref:Microsoft.Build.Tasks.GenerateManifestBase.Platform%2A>|Debe ser **AnyCPU**, **x86**, **x64** o **Itanium**.  Se aceptan cadenas vacías.|  
|<xref:Microsoft.Build.Tasks.GenerateApplicationManifest.ManifestType%2A>|Debe ser **Nativo** o **ClickOnce**.|  
|<xref:Microsoft.Build.Tasks.GenerateManifestBase.TargetCulture%2A>|Puede ser una cadena vacía.  También puede ser una referencia cultural neutra \(especificada por el código de idioma de dos caracteres en minúsculas, por ejemplo, "jp" para japonés\).  De lo contrario, este valor tiene los mismos requisitos que <xref:System.Globalization.CultureInfo.%23ctor%2A>.|  
|<xref:Microsoft.Build.Tasks.GenerateApplicationManifest.TargetFrameworkVersion%2A>|Debe tener el formato v*\#*.*\#*.  Debe ser posterior a v2.0.  Se aceptan cadenas vacías.|  
  
 Cuando la tarea es <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest>, se aplican los requisitos siguientes:  
  
|Parámetro|Requisitos|  
|---------------|----------------|  
|<xref:Microsoft.Build.Tasks.GenerateManifestBase.AssemblyName%2A>|Debe ser un nombre de archivo válido.|  
|<xref:Microsoft.Build.Tasks.GenerateManifestBase.AssemblyVersion%2A>|Tiene los mismos requisitos que <xref:System.Version.%23ctor%2A>.  Todos los octetos deben ser mayores que 0.  Debe especificar los cuatro octetos.  Se aceptan cadenas vacías.|  
|<xref:Microsoft.Build.Tasks.GenerateDeploymentManifest.MinimumRequiredVersion%2A>|Tiene los mismos requisitos que <xref:System.Version.%23ctor%2A>.  Todos los octetos deben ser mayores que 0.  Se aceptan cadenas vacías.|  
|<xref:Microsoft.Build.Tasks.GenerateManifestBase.Platform%2A>|Debe ser **AnyCPU**, **x86**, **x64** o **Itanium**.  Se aceptan cadenas vacías.|  
|<xref:Microsoft.Build.Tasks.GenerateManifestBase.TargetCulture%2A>|Puede ser una cadena vacía.  También puede ser una referencia cultural neutra \(especificada por el código de idioma de dos caracteres en minúsculas, por ejemplo, "jp" para japonés\).  De lo contrario, este valor tiene los mismos requisitos que <xref:System.Globalization.CultureInfo.%23ctor%2A>.|  
|<xref:Microsoft.Build.Tasks.GenerateDeploymentManifest.UpdateMode%2A>|Debe ser **Primer plano** o **Fondo**.  Se aceptan cadenas vacías.|  
|<xref:Microsoft.Build.Tasks.GenerateDeploymentManifest.UpdateUnit%2A>|Debe ser **Horas**, **Días** o **Semanas**.  Se aceptan cadenas vacías.|  
  
## Vea también  
 <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.ApplicationManifest.HostInBrowser%2A>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.TargetFrameworkVersion%2A>   
 [Referencia de esquemas de productos y paquetes](../deployment/product-and-package-schema-reference.md)   
 [Panel Publicar, Diseñador de proyectos](../ide/reference/publish-page-project-designer.md)   
 [Error de MSBuild MSB3116](../misc/msbuild-error-msb3116.md)   
 [Error de MSBuild MSB3117](../misc/msbuild-error-msb3117.md)   
 [Error de MSBuild MSB3118](../misc/msbuild-error-msb3118.md)   
 [Error de MSBuild MSB3185](../misc/msbuild-error-msb3185.md)