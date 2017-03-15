---
title: "Error de MSBuild MSB3166 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.PackageResourceFileNotFound"
  - "vsdeploy.chm:13166"
helpviewer_keywords: 
  - "MSB3166"
ms.assetid: f5dff83a-1e41-4c92-a137-89b7e9f3cd93
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3166
**MSB3166: No se pudo encontrar el archivo requerido '\<archivo\>' para el elemento '\<paquete\>'.**  
  
 Este error se genera si falta un contrato de licencia para el usuario final \(CLUF\) o el archivo de comprobación de externo.  Asegúrese de que el archivo está en el disco.  
  
### Para corregir este error  
  
-   Vuelva a instalar el SDK de Visual Studio  
  
     \-O bien\-  
  
-   Copie los archivos necesarios en la ubicación adecuada.  
  
## Vea también  
 [\<PackageFiles\> \(Elemento\)](../deployment/packagefiles-element-bootstrapper.md)