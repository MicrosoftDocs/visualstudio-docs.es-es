---
title: "Could not create output directory &#39;directory&#39;. &lt;reason&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cannot_create_output_dir"
ms.assetid: b4d1d19f-f582-49d0-a9a9-d3f4ce0a447b
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Could not create output directory &#39;directory&#39;. &lt;reason&gt;
El sistema del proyecto no puede crear un directorio del proyecto.  
  
 El sistema del proyecto intentará crear todos los directorios de resultados en cuanto se abra el proyecto.  A continuación se muestra una lista de los directorios de resultados creados por el sistema del proyecto:  
  
 \\\\obj\\*del projectfolder*\\`configname`  
 Directorio temporal de resultados específico de la configuración.  
  
 *carpetaDelProyecto*\\obj\\`configname`\\temp  
 Área de trabajo que utiliza el compilador.  
  
 *carpetaDelProyecto*\\obj\\`configname`\\temppe  
 Aquí se crean los ensamblados temporales que utilizan los diseñadores en el tiempo de diseño.  
  
 outputdir  
 Directorio especificado por la propiedad Ruta de acceso de los resultados.  Vea [Compilar \(Página, Diseñador de proyectos\) \(C\#\)](../ide/reference/build-page-project-designer-csharp.md) para obtener más información.  
  
 La causa más común de que se produzca un error al crear uno de los directorios bajo la carpeta obj es que se supere el límite MAX\_PATH para nombres de directorios.  
  
 Entre las causas menos comunes se incluyen el permiso denegado y el espacio en disco insuficiente.  
  
 **Para corregir este error**  
  
-   Si la ruta de acceso es demasiado larga, cambie la ubicación del proyecto o reduzca el nombre de la configuración del proyecto.  
  
     El proceso de compilación no finalizará correctamente si ocurre este error.  
  
## Vea también  
 [NIB How to: Modify Project Properties and Configuration Settings](http://msdn.microsoft.com/es-es/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)