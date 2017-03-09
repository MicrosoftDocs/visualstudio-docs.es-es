---
title: "At least one configuration was not loaded because it does not have a configuration name attribute | Microsoft Docs"
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
  - "vs.tasklisterror.projfile_nameless_config"
ms.assetid: 711f7253-308b-44e0-b8bc-ca5c16536a2c
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# At least one configuration was not loaded because it does not have a configuration name attribute
Cada sección `<Config>` en un archivo .csproj o .vbproj debe tener un atributo Name que defina un nombre exclusivo para esa configuración.  Este diagnóstico indica que falta el atributo Name.  Si falta el atributo Name de una configuración, dicha configuración no se cargará en el proyecto.  
  
 Es muy probable que el error esté causado por la edición manual del archivo de proyecto.  
  
 **Para corregir este error**  
  
-   Inserte un nombre de configuración justo después de la línea `<Config>` en el archivo de proyecto.  
  
    ```  
    Name = "someconfigname"  
    ```  
  
     Un nombre típico de configuración es `Debug` o `Release`.  
  
## Vea también  
 [Archivos de proyecto](/visual-cpp/ide/project-files)   
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/es-es/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)