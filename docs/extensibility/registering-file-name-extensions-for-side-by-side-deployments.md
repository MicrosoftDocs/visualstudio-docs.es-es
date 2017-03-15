---
title: "Registrar extensiones de nombre de archivo para las implementaciones en paralelo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "extensiones de archivo, registro de side-by-side"
ms.assetid: 9ab046a2-147d-4167-aa14-7d661b1eaaa5
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Registrar extensiones de nombre de archivo para las implementaciones en paralelo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Para VSPackages implementado en un entorno, debe registrar las extensiones de nombre de archivo para asociar los archivos de la versión correcta de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. A menos que utilice una extensión de nombre de archivo específico de la versión, el registro permite a los usuarios abrir el proyecto y archivos de proyecto elemento en la versión adecuada de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## En esta sección  
 [Acerca de las extensiones de nombre de archivo](../extensibility/about-file-name-extensions.md)  
 Describe cómo se registran las extensiones de nombre de archivo.  
  
 [Especificar los controladores de archivo para las extensiones de nombre de archivo](../extensibility/specifying-file-handlers-for-file-name-extensions.md)  
 Proporciona información sobre cómo registrar las aplicaciones que pueden abrir, editar etc., una extensión de nombre de archivo en particular.  
  
 [Registrar los verbos de extensiones de nombre de archivo](../extensibility/registering-verbs-for-file-name-extensions.md)  
 Describe cómo registrar los verbos.  
  
 [Administrar asociaciones de archivos en paralelo](../extensibility/managing-side-by-side-file-associations.md)  
 Describe cómo controlar las instalaciones en paralelo en el que una versión determinada de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] debe invocarse para abrir un archivo.  
  
## Secciones relacionadas  
 [Compatibilidad con varias versiones de Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)  
 Describe los problemas relacionados con varias versiones de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y su VSPackage durante el desarrollo y la implementación en usuarios finales.