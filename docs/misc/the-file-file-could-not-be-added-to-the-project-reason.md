---
title: "No se pudo agregar el archivo &#39;archivo&#39; al proyecto. &lt;motivo&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.projfile_no_add_file"
ms.assetid: 8bd70556-596a-4e24-a71c-a340604ee93d
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# No se pudo agregar el archivo &#39;archivo&#39; al proyecto. &lt;motivo&gt;
No se puede agregar al proyecto un archivo que se ha leído desde el archivo .vbproj o .csproj. Entre los motivos se incluyen:  
  
-   Nombre de archivo no válido.  
  
-   Archivo dentro de una ruta de acceso. Por ejemplo, si tiene una ruta de acceso relativa al proyecto de File1\\File2.txt, pero también hay una carpeta con la ruta de acceso relativa de File1\\File2.txt.  
  
-   El elemento ya existe. Esto se produce cuando un archivo aparece dos veces en el archivo del proyecto.  
  
-   El vínculo ya existe. El sistema del proyecto [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] y [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] tiene una limitación que consiste en que solo puede haber un vínculo con el mismo nombre por proyecto. Por ejemplo, esto significa que no puede tener un vínculo al archivo file.vb en la carpeta A y la carpeta B del proyecto a la vez.  
  
 Este error se debe probablemente a la edición manual del archivo del proyecto.  
  
 Cualquier archivo para el que se muestre este diagnóstico no se agregará al proyecto.  
  
## Vea también  
 [Archivos de proyecto](/visual-cpp/ide/project-files)   
 [NIB: administración elementos en proyectos](http://msdn.microsoft.com/es-es/762e606b-7f44-4b66-97a1-e30a703654a0)