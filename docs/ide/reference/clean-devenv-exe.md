---
title: "/Clean (devenv.exe) | Microsoft Docs"
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
  - "/clean (modificador para Devenv)"
  - "compilaciones [Team System], limpiar archivos"
  - "clean (modificador para Devenv)"
  - "Devenv, /clean (modificador)"
ms.assetid: 79929dfd-22c9-4cec-a0d0-a16f15b8f7e4
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Clean (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Limpia todos los directorios de resultados y archivos intermedios.  
  
## Sintaxis  
  
```  
devenv FileName /Clean [ /project projectnameorfile [/projectconfig name ] ]  
```  
  
## Argumentos  
 `FileName`  
 Obligatorio.  Ruta de acceso completa y nombre del archivo de solución o del archivo de proyecto.  
  
 \/project `ProjName`  
 Opcional.  Ruta de acceso y nombre de un archivo de proyecto dentro de la solución.  Puede escribir una ruta de acceso relativa desde la carpeta `SolutionName` hasta el archivo de proyecto, el nombre para mostrar del proyecto, o la ruta de acceso y el nombre completos del archivo de proyecto.  
  
 \/projectconfig `ProjConfigName`  
 Opcional.  Nombre de la configuración de compilación de proyecto que se utilizará cuando se limpie el proyecto especificado en `/project`.  
  
## Comentarios  
 Este modificador realiza la misma función que el comando de menú **Limpiar solución** dentro del entorno de desarrollo integrado \(IDE\).  
  
 Las cadenas que incluyan espacios en blanco deben aparecer entre comillas dobles.  
  
 La información de resumen de las limpiezas y las compilaciones, incluidos los errores, puede mostrarse en la ventana de **Comando** o en cualquier archivo de registro especificado con el modificador `/out`.  
  
## Ejemplo  
 En el primer ejemplo se limpia la solución `MySolution`, utilizando la configuración predeterminada especificada en el archivo de solución.  
  
 En el segundo ejemplo se limpia el proyecto `CSharpConsoleApp`, utilizando la configuración de compilación de proyecto `Debug` contenida en la configuración de soluciones `Debug` de `MySolution`.  
  
```  
Devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /Clean  
  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /Clean /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig "Debug"   
```  
  
## Vea también  
 [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [\/Build](../../ide/reference/build-devenv-exe.md)   
 [\/Rebuild](../../ide/reference/rebuild-devenv-exe.md)   
 [\/Out](../../ide/reference/out-devenv-exe.md)