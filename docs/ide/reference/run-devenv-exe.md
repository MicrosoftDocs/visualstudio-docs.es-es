---
title: "/Run (devenv.exe) | Microsoft Docs"
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
  - "/r (modificador para Devenv)"
  - "/run (Devenv)"
  - "aplicaciones [Visual Studio], ejecutar"
  - "Devenv, /run (modificador)"
  - "r (modificador para Devenv: /r)"
  - "run (modificador para Devenv)"
ms.assetid: b1f22f9d-39a5-4918-8a2a-4b5c1e872665
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Run (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Compila y ejecuta el proyecto o la solución que ha especificado.  
  
## Sintaxis  
  
```  
devenv {/run|/r} {SolutionName|ProjectName}  
```  
  
## Argumentos  
 `SolutionName`  
 Obligatorio.  Ruta de acceso y nombre completos de un archivo de solución.  
  
 `ProjectName`  
 Obligatorio.  Ruta de acceso y nombre completos de un archivo de proyecto.  
  
## Comentarios  
 Compila y, a continuación, ejecuta la solución o el proyecto especificados según los valores establecidos para la configuración de solución activa.  Este modificador inicia el entorno de desarrollo integrado \(IDE\) y lo deja activo una vez que se ha completado la ejecución del proyecto o la solución.  
  
-   Las cadenas que incluyan espacios en blanco deben aparecer entre comillas dobles.  
  
-   La información de resumen, incluidos los errores, puede mostrarse en la ventana **Comando** o en cualquier archivo de registro especificado con el modificador `/out`.  
  
## Ejemplo  
 Este ejemplo ejecuta la solución `MySolution` con la configuración de implementación activa.  
  
```  
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln"  
```  
  
## Vea también  
 [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [\/Runexit](../../ide/reference/runexit-devenv-exe.md)   
 [\/Build](../../ide/reference/build-devenv-exe.md)   
 [\/Rebuild](../../ide/reference/rebuild-devenv-exe.md)   
 [\/Out](../../ide/reference/out-devenv-exe.md)