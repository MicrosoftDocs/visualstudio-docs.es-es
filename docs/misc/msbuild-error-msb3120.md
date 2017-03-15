---
title: "Error de MSBuild MSB3120 | Microsoft Docs"
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
  - "GenerateManifest.FileAssociationExtensionTooLong"
helpviewer_keywords: 
  - "MSB3120"
ms.assetid: 20bc64f5-aadc-4eec-9915-a87a3d7f81ea
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3120
**MSB3120: La extensión de asociación de archivo '\< extensión \>' supera la longitud máxima permitida de \<longitud máxima\>.**  
  
 El número de caracteres de la extensión de asociación de archivo no debe superar el número indicado.  
  
### Para corregir este error  
  
-   Establezca el atributo [Manifiesto de la implementación ClickOnce](../deployment/clickonce-deployment-manifest.md)`extension` en un valor que no contenga más caracteres que el límite permitido para el sistema operativo de destino.  
  
## Vea también  
 [Panel Publicar, Diseñador de proyectos](../ide/reference/publish-page-project-designer.md)   
 [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)