---
title: "Error de MSBuild MSB3254 | Microsoft Docs"
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
  - "MSB3254"
ms.assetid: cb9636b2-d9b3-466d-959c-14c7c8017a78
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3254
**MSB3254: Se omitirá el archivo \<nombre\> porque no se puede leer.  Bien se pasó a InstalledAssemblySubsetTables o bien se encontró al buscar en la carpeta \<nombre\> de TargetFrameworkDirectories.**  
  
 Este error se produce cuando no se puede leer el archivo XML client.xml de [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)].  El archivo no se puede leer porque está dañado, bloqueado o por algún otro problema.  
  
 [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)] es un subconjunto de la biblioteca completa en tiempo de ejecución de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 3.5.  Para obtener más información acerca de [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)], vea [.NET Framework Client Profile](../Topic/.NET%20Framework%20Client%20Profile.md).  
  
 Procedimientos  
  
### Para corregir este error  
  
-   Asegúrese de que tiene permisos completos y acceso total al archivo, o bien instale de nuevo la biblioteca redistribuible en tiempo de ejecución de [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)] para reemplazar el archivo dañado.  
  
## Vea también  
 [Elemento Project \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [Recursos adicionales](../msbuild/additional-msbuild-resources.md)