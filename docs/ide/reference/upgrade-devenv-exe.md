---
title: "/Upgrade (devenv.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "/upgrade (modificador para Devenv)"
  - "Devenv, /upgrade (modificador)"
  - "upgrade (modificador para Devenv)"
ms.assetid: 3468045c-5cc9-4157-9a9d-622452145d27
caps.latest.revision: 18
caps.handback.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Upgrade (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Actualiza el archivo de solución y todos sus archivos de proyecto, o el archivo de proyecto especificado, a los formatos actuales de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para estos archivos.  
  
## Sintaxis  
  
```  
devenv SolutionFile | ProjectFile /upgrade  
```  
  
## Argumentos  
 `SolutionFile`  
 Necesario si va a actualizar una solución completa y sus proyectos.  Ruta de acceso y nombre de un archivo de solución.  Se puede escribir solo el nombre del archivo de solución o una ruta de acceso completa y el nombre del archivo de solución.  Si la carpeta o el archivo especificados no existen todavía, se crean.  
  
 `ProjectFile`  
 Necesario si va a actualizar un único proyecto.  Ruta de acceso y nombre de un archivo de proyecto dentro de la solución.  Se puede escribir solo el nombre del archivo de proyecto o una ruta de acceso completa y el nombre del archivo de proyecto.  Si la carpeta o el archivo especificados no existen todavía, se crean.  
  
## Comentarios  
 Se crean automáticamente copias de seguridad y se copian en un directorio denominado Backup que se crea en el directorio actual.  
  
 Se deben desproteger las soluciones o los proyectos bajo el control de código fuente antes de poderse actualizar.  
  
 Al utilizar el modificador `/upgrade` no se inicia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  Los resultados de la actualización se pueden ver en el informe de actualización para el lenguaje de desarrollo de la solución o el proyecto.  No se devuelve ninguna información de error o de uso.  Para obtener más información sobre cómo actualizar proyectos en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], vea [Cómo: Solucionar problemas de actualizaciones de proyecto de Visual Studio incorrectas](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md).  
  
## Ejemplo  
 En este ejemplo se actualiza un archivo de solución denominado "MyProject.sln" en la carpeta predeterminada para las soluciones de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
```  
devenv "MyProject.sln" /upgrade  
```  
  
## Vea también  
 [Cómo: Solucionar problemas de actualizaciones de proyecto de Visual Studio incorrectas](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md)   
 [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)