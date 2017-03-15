---
title: "Error de MSBuild MSB3255 | Microsoft Docs"
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
  - "MSB3255"
ms.assetid: baac844e-a662-4421-bed1-2bc98f2e1cdf
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3255
**MSB3255: No se encontraron archivos del subconjunto de la versión de .NET Framework de destino en los directorios de la versión de .NET Framework de destino ni en las ubicaciones especificadas en InstalledAssemblySubsetTables.**  
  
 Este error se produce cuando un nombre se pasa en la propiedad <xref:Microsoft.Build.Tasks.ResolveAssemblyReference.FullTargetFrameworkSubsetNames%2A>, pero no se puede encontrar ningún subconjunto con ese nombre.  
  
 [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)] es un subconjunto de la biblioteca completa en tiempo de ejecución de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 3.5.  Para obtener más información acerca de [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)], vea [.NET Framework Client Profile](../Topic/.NET%20Framework%20Client%20Profile.md).  
  
 Procedimientos  
  
### Para corregir este error  
  
-   Incluya una copia del archivo del subconjunto en la carpeta de la versión de .NET Framework de destino o en una de las ubicaciones especificadas en <xref:Microsoft.Build.Tasks.ResolveAssemblyReference.InstalledAssemblySubsetTables%2A>.  
  
## Vea también  
 [Elemento Project \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [Recursos adicionales](../msbuild/additional-msbuild-resources.md)