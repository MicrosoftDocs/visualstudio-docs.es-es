---
title: "At least one file is missing the &#39;attribute&#39; attribute | Microsoft Docs"
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
  - "vs.tasklisterror.projfile_missing_file_attrib"
ms.assetid: 2627974b-c9cd-4d85-9af4-dd3811214ea4
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# At least one file is missing the &#39;attribute&#39; attribute
A un nodo de archivo leído desde el archivo .vbproj o .csproj le faltan algunos atributos requeridos por el sistema del proyecto.  Actualmente, el único atributo con esas características es `RelPath`, que especifica la ubicación del archivo bajo la carpeta de proyecto.  
  
 Es muy probable que el error esté causado por la edición manual del archivo de proyecto.  
  
 **Para corregir este error**  
  
-   Quite del archivo de proyecto el nodo del archivo afectado.  Además, si el archivo continúa en el disco, puede cambiar al modo **Mostrar todos los archivos** \(haga clic el botón correspondiente del Explorador de soluciones\), hacer clic con el botón secundario del mouse en el archivo afectado y seleccionar **Incluir en el proyecto**.  
  
     No se agregará al proyecto ningún archivo al que le falte el atributo `RelPath`.  
  
## Vea también  
 [Archivos de proyecto](/visual-cpp/ide/project-files)   
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/es-es/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)