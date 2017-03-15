---
title: "/Rebuild (devenv.exe) | Microsoft Docs"
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
  - "/rebuild (modificador para Devenv)"
  - "aplicaciones [Visual Studio], recompilar"
  - "Devenv, /rebuild (modificador)"
  - "proyectos [Visual Studio], recompilar"
  - "rebuild (modificador /rebuild para Devenv)"
ms.assetid: c5a8a4bf-0e2b-46eb-a44a-8aeb29b92c32
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Rebuild (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Limpia y, a continuación, compila la configuración de solución especificada.  
  
## Sintaxis  
  
```  
devenv SolutionName /rebuild SolnConfigName [/project ProjName] [/projectconfig ProjConfigName]  
```  
  
## Argumentos  
 `SolnConfigName`  
 Requerido.  Nombre de la configuración de solución que se utilizará para recompilar la solución indicada en `SolutionName`.  
  
 `SolutionName`  
 Requerido.  Ruta de acceso y nombre completos del archivo de solución.  
  
 \/project `ProjName`  
 Opcional.  Ruta de acceso y nombre de un archivo de proyecto dentro de la solución.  Puede escribir una ruta de acceso relativa desde la carpeta `SolutionName` hasta el archivo de proyecto, el nombre para mostrar del proyecto, o la ruta de acceso y el nombre completos del archivo de proyecto.  
  
 \/projectconfig `ProjConfigName`  
 Opcional.  Nombre de la configuración de compilación de proyecto que se utilizará cuando se recompile el proyecto especificado en `/project`.  
  
## Comentarios  
  
-   Este modificador realiza la misma función que el comando de menú **Recompilar solución** dentro del entorno de desarrollo integrado \(IDE\).  
  
-   Las cadenas que incluyan espacios en blanco deben aparecer entre comillas dobles.  
  
-   La información de resumen de las limpiezas y las compilaciones, incluidos los errores, puede mostrarse en la ventana de **Comando** o en cualquier archivo de registro especificado con el modificador `/out`.  
  
## Ejemplo  
 En este ejemplo se limpia y se recompila el proyecto `CSharpWinApp`, utilizando la configuración de compilación de proyecto `Debug` contenida en la configuración de soluciones `Debug` de `MySolution`.  
  
```  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /rebuild Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug   
```  
  
## Vea también  
 [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [\/Build](../../ide/reference/build-devenv-exe.md)   
 [\/Clean](../../ide/reference/clean-devenv-exe.md)   
 [\/Out](../../ide/reference/out-devenv-exe.md)