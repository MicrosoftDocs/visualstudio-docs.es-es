---
title: "/Deploy (devenv.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "/deploy (modificador para Devenv)"
  - "deploy (modificador para Devenv)"
  - "implementar aplicaciones [Visual Studio], después de la compilación"
  - "Devenv, /deploy (modificador)"
ms.assetid: e47c8723-df08-4645-aa2d-0c956e7ccca2
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Deploy (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Implementa una solución después de una compilación o recompilación.  Sólo se aplica a los proyectos de código administrado.  
  
## Sintaxis  
  
```  
devenv SolutionName /deploy SolnConfigName [/project ProjName] [/projectconfig ProjConfigName] [/out LogFileName]  
```  
  
## Argumentos  
 `SolnConfigName`  
 Obligatorio.  Nombre de la configuración de solución que se utilizará para compilar la solución indicada en `SolutionName`.  
  
 `SolutionName`  
 Obligatorio.  Ruta de acceso y nombre completos del archivo de solución.  
  
 \/project `ProjName`  
 Opcional.  Ruta de acceso y nombre de un archivo de proyecto dentro de la solución.  Puede escribir una ruta de acceso relativa desde la carpeta `SolutionName` hasta el archivo de proyecto, el nombre para mostrar del proyecto, o la ruta de acceso y el nombre completos del archivo de proyecto.  
  
 \/projectconfig `ProjConfigName`  
 Opcional.  Nombre de la configuración de compilación de proyecto que se utilizará cuando se compile el proyecto especificado en `/project`.  
  
## Comentarios  
 El proyecto especificado debe ser un proyecto de implementación.  Si el proyecto especificado no es un proyecto de implementación, al pasar el proyecto que se ha compilado para implementación, se produce un error.  
  
 Las cadenas que incluyan espacios en blanco deben aparecer entre comillas dobles.  
  
 La información de resumen de las compilaciones, incluidos los errores, puede mostrarse en la ventana de **Comando** o en cualquier archivo de registro especificado con el modificador `/out`.  
  
## Ejemplo  
 En este ejemplo se implementa el proyecto `CSharpConsoleApp`, utilizando la configuración de compilación de proyecto `Release` contenida en la configuración de soluciones `Release` de `MySolution`.  
  
```  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /deploy Release /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Release   
```  
  
## Vea también  
 [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [\/Project](../../ide/reference/project-devenv-exe.md)   
 [\/Build](../../ide/reference/build-devenv-exe.md)   
 [\/Clean](../../ide/reference/clean-devenv-exe.md)   
 [\/Rebuild](../../ide/reference/rebuild-devenv-exe.md)   
 [\/Out](../../ide/reference/out-devenv-exe.md)