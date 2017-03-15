---
title: "The user options settings file for this project is missing the &#39;section&#39; section | Microsoft Docs"
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
  - "vs.tasklisterror.peruserfile_sectionerr"
ms.assetid: 576070f5-76b6-46e4-8aba-83442521027f
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The user options settings file for this project is missing the &#39;section&#39; section
Falta el nodo Build del archivo .vbproj.user o .csproj.user.  
  
 La sección Build abarca la configuración de depuración.  Si falta esta sección, no se cargará la configuración de depuración del usuario y tomará valores predeterminados.  
  
 Es muy probable que la situación esté causada por la edición manual del archivo de proyecto.  
  
 El sistema del proyecto volverá a escribir automáticamente el archivo de proyecto de cada usuario cuando se cierre el proyecto.  
  
 Esta advertencia sólo tiene valor informativo.  
  
## Vea también  
 [Archivos de proyecto](/visual-cpp/ide/project-files)   
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/es-es/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)