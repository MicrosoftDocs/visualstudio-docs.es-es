---
title: "/Build (devenv.exe) | Microsoft Docs"
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
  - "/build (modificador para Devenv)"
  - "build (modificador para Devenv)"
  - "compilaciones [Team System], línea de comandos"
  - "Devenv, /build (modificador)"
ms.assetid: ced21627-7653-455b-8821-3e31c6a448cf
caps.latest.revision: 15
caps.handback.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Build (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Compila una solución mediante un archivo de configuración de soluciones especificado.  
  
## Sintaxis  
  
```  
Devenv SolutionName /build SolnConfigName [/project ProjName [/projectconfig ProjConfigName]]  
```  
  
## Argumentos  
 `SolutionName`  
 Obligatorio.  Ruta de acceso y nombre completos del archivo de solución.  
  
 `SolnConfigName`  
 Obligatorio.  Nombre de la configuración de solución que se utilizará para compilar la solución indicada en `SolutionName`.  
  
 \/project `ProjName`  
 Opcional.  Ruta de acceso y nombre de un archivo de proyecto dentro de la solución.  Puede escribir una ruta de acceso relativa desde la carpeta `SolutionName` hasta el archivo de proyecto, el nombre para mostrar del proyecto, o la ruta de acceso y el nombre completos del archivo de proyecto.  
  
 \/projectconfig `ProjConfigName`  
 Opcional.  Nombre de la configuración de compilación de proyecto que se utilizará cuando se compile el proyecto especificado en `/project`.  
  
## Comentarios  
 Este modificador realiza la misma función que el comando de menú **Generar solución** dentro del entorno de desarrollo integrado \(IDE\).  
  
 Las cadenas que incluyan espacios en blanco deben aparecer entre comillas dobles.  
  
 La información de resumen de las compilaciones, incluidos los errores, puede mostrarse en la ventana de **Comando** o en cualquier archivo de registro especificado con el modificador `/out`.  
  
 Este comando solo compila los proyectos que han cambiado desde la última compilación.  Para compilar todos los proyectos en una solución, utilice [\/Rebuild](../../ide/reference/rebuild-devenv-exe.md).  
  
## Ejemplo  
 En este ejemplo se compila el proyecto `CSharpConsoleApp`, utilizando la configuración de compilación de proyecto `Debug` contenida en la configuración de soluciones `Debug` de `MySolution`.  
  
```  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug   
```  
  
## Vea también  
 [Compilar y limpiar proyectos y soluciones en Visual Studio](../../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)   
 [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [\/Rebuild](../../ide/reference/rebuild-devenv-exe.md)   
 [\/Clean](../../ide/reference/clean-devenv-exe.md)   
 [\/Out](../../ide/reference/out-devenv-exe.md)