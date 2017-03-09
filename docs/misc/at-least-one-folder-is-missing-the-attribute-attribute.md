---
title: "At least one folder is missing the &#39;attribute&#39; attribute | Microsoft Docs"
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
  - "vs.tasklisterror.projfile_missing_fold_attrib"
ms.assetid: 3a0498a9-df61-47d8-a228-f88f4f138df8
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# At least one folder is missing the &#39;attribute&#39; attribute
A un nodo de carpeta que se ha leído desde el archivo .vbproj o .csproj le faltan algunos atributos requeridos por el sistema del proyecto.  Actualmente, el único atributo con esas características es **RelPath**, que especifica en qué lugar de la carpeta de proyecto se encuentra la carpeta en cuestión.  
  
 Es muy probable que el error esté causado por la edición manual del archivo de proyecto.  
  
 **Para corregir este error**  
  
-   Quite del archivo de proyecto el nodo de la carpeta afectada.  Además, si la carpeta continúa en el disco, puede cambiar al modo Mostrar todos los archivos \(haga clic el botón correspondiente del Explorador de soluciones\), hacer clic con el botón secundario del mouse en la carpeta afectada y elegir **Incluir en el proyecto**.  
  
     No se agregará al proyecto ninguna carpeta a la que le falte un atributo.  
  
## Vea también  
 [Archivos de proyecto](/visual-cpp/ide/project-files)   
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/es-es/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)