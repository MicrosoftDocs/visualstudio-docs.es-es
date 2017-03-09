---
title: "The project file is missing the &#39;section&#39; section | Microsoft Docs"
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
  - "vs.tasklisterror.projfile_sectionerr"
ms.assetid: 516ab410-1b73-4539-9654-6323af6135b2
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The project file is missing the &#39;section&#39; section
El archivo .vbproj o .csproj está dañado.  Falta una de las siguientes secciones:  
  
-   Compilar  
  
-   Files \(Archivos\)  
  
-   VisualStudio  
  
-   VisualBasic o CSHARP  
  
 Si faltan las secciones VisualStudio, VisualBasic o CSHARP, el proyecto no se cargará.  Si falta la sección Build o Files, el archivo de proyecto se cargará como se muestra a continuación:  
  
-   Si falta Build, se perderán todos los valores de generación y la información de configuración.  
  
-   Si falta Files, el proyecto no contendrá archivos.  
  
 **Para corregir este error**  
  
-   Cree de nuevo el proyecto.  
  
## Vea también  
 [Archivos de proyecto](/visual-cpp/ide/project-files)   
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/es-es/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)