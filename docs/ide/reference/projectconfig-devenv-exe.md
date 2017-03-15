---
title: "/ProjectConfig (devenv.exe) | Microsoft Docs"
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
  - "/projectconfig (modificador para Devenv)"
  - "configuraciones de compilación, especificar"
  - "configuraciones, limpiar"
  - "configuraciones, recompilar"
  - "proyectos de implementación, agregar"
  - "proyectos de implementación, crear"
  - "proyectos de implementación, especificar"
  - "Devenv, /projectconfig (modificador)"
  - "projectconfig (modificador /projectconfig para Devenv)"
  - "proyectos [Visual Studio], configuración de compilación"
  - "proyectos [Visual Studio], limpiar"
ms.assetid: 6b54ef59-ffed-4f62-a645-1279ede97ebf
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /ProjectConfig (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Especifica la configuración de compilación de proyecto que se aplicará cuando se compile, se limpie, se recompile o se implemente el proyecto especificado en el argumento `/project`.  
  
## Sintaxis  
  
```  
devenv SolutionName {/build|/clean|/rebuild|/deploy} SolnConfigName [/project ProjName] [/projectconfig ProjConfigName]  
```  
  
## Argumentos  
 \/build  
 Compila el proyecto especificado por `/project` `ProjName`.  
  
 \/clean  
 Limpia todos los archivos intermedios y directorios de resultados creados durante una generación.  
  
 \/rebuild  
 Limpia y, a continuación, compila el proyecto especificado por `/project` `ProjName`.  
  
 \/deploy  
 Especifica que el proyecto se ha de implementar después de compilar o recompilar.  
  
 `SolnConfigName`  
 Obligatorio.  Nombre de la configuración de solución que se aplicará a la solución especificada en `SolutionName`.  
  
 `SolutionName`  
 Obligatorio.  Ruta de acceso y nombre completos del archivo de solución.  
  
 \/project `ProjName`  
 Opcional.  Ruta de acceso y nombre de un archivo de proyecto dentro de la solución.  Puede escribir una ruta de acceso relativa desde la carpeta `SolutionName` hasta el archivo de proyecto, el nombre para mostrar del proyecto, o la ruta de acceso y el nombre completos del archivo de proyecto.  
  
 \/projectconfig `ProjConfigName`  
 Opcional.  Nombre de la configuración de compilación de proyecto que se aplicará al proyecto especificado en `/project`.  
  
## Comentarios  
  
-   Debe utilizarse con el modificador `/project` como parte de un comando `devenv /build`, \/`clean`, `/rebuild` o `/deploy`.  
  
-   Las cadenas que incluyan espacios en blanco deben aparecer entre comillas dobles.  
  
-   La información de resumen de las compilaciones, incluidos los errores, puede mostrarse en la ventana de **Comando** o en cualquier archivo de registro especificado con el modificador `/out`.  
  
## Ejemplo  
 En este ejemplo se compila el proyecto `CSharpConsoleApp`, utilizando la configuración de compilación de proyecto `Debug` contenida en la configuración de soluciones `Debug` de `MySolution`.  
  
```  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug   
```  
  
## Vea también  
 [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [\/Project](../../ide/reference/project-devenv-exe.md)   
 [\/Build](../../ide/reference/build-devenv-exe.md)   
 [\/Clean](../../ide/reference/clean-devenv-exe.md)   
 [\/Rebuild](../../ide/reference/rebuild-devenv-exe.md)   
 [\/Deploy](../../ide/reference/deploy-devenv-exe.md)   
 [\/Out](../../ide/reference/out-devenv-exe.md)