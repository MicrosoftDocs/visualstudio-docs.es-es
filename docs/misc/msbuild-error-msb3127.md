---
title: "Error de MSBuild MSB3127 | Microsoft Docs"
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
  - "GenerateManifest.FileAssociationDefaultIconNotInstalled"
helpviewer_keywords: 
  - "MSB3127"
ms.assetid: 161eea9a-332f-463e-a49e-d4030e937d52
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3127
**MSB3127: No se encuentra el icono predeterminado \< nombre icono \> en las referencias de archivo actuales, o bien no forma parte del grupo de descargas necesario.  El nombre de archivo del icono predeterminado distingue mayúsculas y minúsculas; por tanto, el nombre al que se hace referencia en el manifiesto de aplicación debe coincidir exactamente con el nombre de archivo del icono.**  
  
 Al publicar una aplicación configurada para utilizar asociaciones de archivo, el icono predeterminado al que se hace referencia en el manifiesto se debe encontrar en las referencias de archivo o debe formar parte del grupo de descargas necesario.  El icono predeterminado es el icono que aparece para los archivos que tienen la asociación de archivo configurada \(la extensión de nombre de archivo configurada\).  
  
### Para corregir este error  
  
-   Agregue el archivo de icono al proyecto actual e inclúyalo en el grupo de descargas necesario.  Para obtener más información, vea [Cómo: Especificar los archivos que se van a publicar mediante ClickOnce](../deployment/how-to-specify-which-files-are-published-by-clickonce.md).  
  
## Vea también  
 [Panel Publicar, Diseñador de proyectos](../ide/reference/publish-page-project-designer.md)