---
title: "The folder &#39;folder&#39; could not be added to the project. &lt;reason&gt; | Microsoft Docs"
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
  - "vs.tasklisterror.projfile_no_add_folder"
ms.assetid: 3f6a5aa7-17cc-4e78-93b7-96e0970e111e
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The folder &#39;folder&#39; could not be added to the project. &lt;reason&gt;
Una carpeta leída desde el archivo .vbproj o .csproj no se puede agregar al proyecto.  Las razones posibles son las siguientes:  
  
-   Nombre no válido  
  
-   Archivo dentro de una ruta de acceso.  Por ejemplo, si tiene una ruta de acceso relativa al proyecto de Folder1\\Folder2\\Folder3, pero también hay un archivo con la ruta de acceso relativa Folder1\\Folder2.  
  
-   El elemento ya existe.  Esto ocurre cuando una carpeta aparece dos veces en el archivo de proyecto.  
  
 Es muy probable que el error esté causado por la edición manual del archivo de proyecto.  
  
 **Para corregir este error**  
  
-   Quite del archivo de proyecto el nodo de la carpeta afectada.  
  
     No se agregarán al proyecto ninguna carpeta, ni archivos bajo la carpeta, para los que se muestre este diagnóstico.  
  
## Vea también  
 [Archivos de proyecto](/visual-cpp/ide/project-files)   
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/es-es/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)